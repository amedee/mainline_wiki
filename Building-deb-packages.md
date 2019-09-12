## Cheat sheet to build .deb packages
`make deb` makes a deb matching the distribution and architecture of the building host.

### To manually make a deb for some other target
1. Create or update a base.tgz for the desired build target  
`pbuilder-dist xenial|bionic|cosmic|disco i386|amd64 create|update`
2. Create/Update the dsc and tar files  
`make deb-src`
3. Get the dsc filename from the output of "make deb-src"  
example: `release/deb-src/mainline_1.0.1.dsc`
4. Build the deb with pbuilder-dist  
template: `pbuilder-dist <dist> <arch> build <dsc_file> --buildresult release/deb`  
example: `pbuilder-dist bionic i386 build release/deb-src/mainline_1.0.1.dsc --buildresult release/deb`

### To build-install-test-uninstall testing debs locally easily without having to get the exact filenames
`make deb-install`  
`make deb-uninstall`
