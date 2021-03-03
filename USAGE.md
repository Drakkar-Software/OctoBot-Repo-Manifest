Example : Add a new supported python version in each project's setup.py
```bash
repo forall -c sed -i '/Programming Language\ \:\:\ Python\ \:\:\ 3\.8/a \ \ \ \ \ \ \ \ \'Programming Language\ \:\:\ Python\ \:\:\ 3\.9\',' setup.py
repo forall -c git checkout -b feature/add-python-3.9-to-setup.py
repo forall -c git add setup.py
repo forall -c git commit -s -m "Add python3.9 to supported version"
repo forall -c 'SSH_URL=$(git remote get-url github | sed "s/git\:\/\/github\.com\//git@github\.com\:/g").git; git remote set-url github $SSH_URL'
repo forall -c git push github --set-upstream feature/add-python-3.9-to-setup.py feature/add-python-3.9-to-setup.py
```
