Example : 

Add a new supported python version in each project's setup.py
```bash
repo forall -c sed -i '/Programming Language\ \:\:\ Python\ \:\:\ 3\.8/a \ \ \ \ \ \ \ \ \'Programming Language\ \:\:\ Python\ \:\:\ 3\.9\',' setup.py
repo forall -c git checkout -b feature/add-python-3.9-to-setup.py
repo forall -c git add setup.py
repo forall -c git commit -s -m "Add python3.9 to supported version"
repo forall -c 'SSH_URL=$(git remote get-url github | sed "s/git\:\/\/github\.com\//git@github\.com\:/g").git; git remote set-url github $SSH_URL'
repo forall -c git push github --set-upstream feature/add-python-3.9-to-setup.py feature/add-python-3.9-to-setup.py
```

Prepare new version
```bash
repo forall -c 'PACKAGE=$(basename $PWD | tr - _ | sed "s/.*/\L&/"); LAST_VERSION=$(git describe --tags --abbrev=0) ; bumpversion --current-version $LAST_VERSION patch $PACKAGE/__init__.py README.md && git add README.md $PACKAGE/__init__.py'
repo forall -c 'CHANGELOG_DATE=`date +"%Y-%m-%d"` ; LAST_VERSION=$(git describe --tags --abbrev=0) ; NEW_VERSION=$(bumpversion --allow-dirty --current-version $LAST_VERSION patch -n --list | grep new_version | sed -r s,"^.*=",,) ; sed -i "/semver\\.org\\/spec\\/v2\\.0\\.0\\.html)\\./a \ \n## [$NEW_VERSION] - $CHANGELOG_DATE \n### Added \n- Python 3.9 support" CHANGELOG.md && git add CHANGELOG.md'
repo forall -c 'LAST_VERSION=$(git describe --tags --abbrev=0) ; bumpversion --current-version $LAST_VERSION patch --commit --allow-dirty --message "[Version] {new_version}"'
```
