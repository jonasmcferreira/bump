#!/bin/sh

set -e

# Parse options:
option_count=0
while getopts "Mmp" bump; do
  case ${bump} in
    p) bump_patch=true; option_count=$((option_count+1));;
    m) bump_minor=true; option_count=$((option_count+1));;
    M) bump_major=true; option_count=$((option_count+1));;
    *)
  esac
done

usage_text="usage: $(basename ${0}) [-Mmp] major.minor.patch"

# Only one incrementation option is allowed:
if [ "$option_count" -ne "1" ]; then
  echo "${usage_text}" && exit 1
fi

# Remove all args except final, non-positional arg (the version number):
shift "$((OPTIND-1))"

# Parse the given version:
first=${1}
vgone=$(echo "${first}" | sed 's/^v//')
clean=$(echo "${vgone}" | awk '{split($0,a,"-"); print a[1]}')
major=$(echo "${clean}" | awk '{split($0,a,"."); print a[1]}')
minor=$(echo "${clean}" | awk '{split($0,a,"."); print a[2]}')
patch=$(echo "${clean}" | awk '{split($0,a,"."); print a[3]}')

# Each element must be populated:
[ -z ${major} ] && echo "${usage_text}" && exit 1
[ -z ${minor} ] && echo "${usage_text}" && exit 1
[ -z ${patch} ] && echo "${usage_text}" && exit 1

# Each element must contain digits only:
[ `echo "${clean}" | sed 's/[0-9]//g'` != ".." ] && echo "${usage_text}" && exit 1

# Add 'v' prefix back if it was supplied originally:
case "$first" in
  v*) clean=$(echo "v${clean}");;
  *);;
esac

# Increment the version number:
[ ! -z ${bump_major} ] && major=$((major+1)) && minor=0 && patch=0
[ ! -z ${bump_minor} ] && minor=$((minor+1)) && patch=0
[ ! -z ${bump_patch} ] && patch=$((patch+1))

# Render final version with 'v' if originally supplied:
final=$(echo "${major}.${minor}.${patch}")
case "$first" in
  v*) final=$(echo "v${final}");;
  *);;
esac

echo "${final}"
