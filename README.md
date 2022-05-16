# work-in-progress RPM packages for cdylib-link-lines

### Steps to build:

- `dnf install -y rpm-build mock`
- Get the latest version:
  `curl -L https://crates.io/api/v1/crates/cdylib-link-lines/0.1.4/download --output cdylib-link-lines-0.1.4.crate`
- rust2rpm to generate the .spec file
- `mkdir -p ~/rpmbuild/SOURCES`
- `cp cdylib-link-lines-0.1.4.crate ~/rpmbuild/SOURCES`
- build SRPM file: `rpmbuild -bs rust-cdylib-link-lines.spec`
- build RPM files: `mock -r fedora-rawhide-x86_64 ~/rpmbuild/SRPMS/rust-cdylib-link-lines-*.src.rpm`
- Resulting packages are here: `/var/lib/mock/fedora-rawhide-x86_64/result/rust-cdylib-link-lines*`

### TODO:

- fix `License` tag to reflect statically linked dependencies
