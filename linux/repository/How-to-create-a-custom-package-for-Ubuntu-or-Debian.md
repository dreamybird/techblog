# How to create a custom package for Debain or Ubuntu

1. Create folders like it:
```bash
tree
.
├── DEBIAN
│   └── control
```

2. Edit DEBIAN/control file

```bash
cat <<EOT > ./DEBIAN/control
Package: qt-creator
Version: 5.4.1-mycompany
Section: base
Priority: optional
Architecture: amd64
Maintainer: My name <myname@mycompany.com>
Description: QT creator for my company.
EOT
```

3. Add into  the folder need files and folders
```bash
tree
.
├── DEBIAN
│   └── control
├── opt
│   └── YourFolder
```

4. Run build your package
```bash
dpkg-deb --build your-package-name
```
