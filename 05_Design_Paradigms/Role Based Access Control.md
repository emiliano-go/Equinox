---
tags:
  - design-paradigms
  - security
  - concept
created: 2026-04-20
---

# Role Based Access Control

The concept of **Role Based Access Control (RBAC)** is based around defining what each role can do outside of function logic.

## Defining Access
Let's imagine we have 3 types of users:
- normal users
- moderators
- admins

Each role should have different access rights.

To define access rights, we can create a `roles.py` file to handle all roles:

```python
ROLES = {
	admin : [
		"read:comments",
		"create:comments",
		"update:comments",
		"delete:comments",
		"delete:users",
	],
	moderator : [
		"read:comments",
		"create:comments",
		"delete:comments",
	],
	user : [
		"read:comments",
		"create:comments",
	],
}
```

Let's imagine we have a simple user model in `app/models.py`.

```python
class User():
	id : str
	role : str
```

We can also create a permission handler function to centralize everything:

```python
from app.models import User

def hasPermission(user : User, permission : str) -> bool:
	user_perms = ROLES[user.role]
	
	if permission not in user_perms:
		return False
	
	return True

```

**Role Based Access Control** is an easy way to design permission for **small applications**.