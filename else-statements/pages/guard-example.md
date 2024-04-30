# Time to Refactor

<!-- Here's the code we ended up with -->
<!-- Let's refactor it to be better -->

````md magic-move
```ts
function createUser(user: User): DatabaseData {
  if (user != null) {
    if (db.isConnected()) {
      if (!db.hasEntry(user.email)) {
        return db.create(user)
      } else {
        throw new Error("user already exists")
      }
    } else {
      throw new Error("database not connected")
    }
  } else {
    throw new Error("user is undefined")
  }
}
```

<!-- First, let's pull out the check of the user object -->

```ts
function createUser(user: User): DatabaseData {
  if (user == null) {
    throw new Error("user is undefined")
  }

  if (db.isConnected()) {
    if (!db.hasEntry(user.email)) {
      return db.create(user)
    } else {
      throw new Error("user already exists")
    }
  } else {
    throw new Error("database not connected")
  }
}
```

<!-- Next, let's check if the database is connected -->

```ts
function createUser(user: User): DatabaseData {
  if (user == null) {
    throw new Error("user is undefined")
  }

  if (!db.isConnected()) {
    throw new Error("database not connected")
  }

  if (!db.hasEntry(user.email)) {
    return db.create(user)
  } else {
    throw new Error("user already exists")
  }
}
```

<!-- Finally, let's check is the user is already in the database -->

```ts
function createUser(user: User): DatabaseData {
  if (user == null) {
    throw new Error("user is undefined")
  }

  if (!db.isConnected()) {
    throw new Error("database not connected")
  }

  if (db.hasEntry(user.email)) {
    throw new Error("user already exists")
  }

  return db.create(user)
}
```

````

<v-click>So much cleaner!</v-click>