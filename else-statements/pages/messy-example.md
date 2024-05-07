# Let's do an example

Adding a new user to a database

<!-- Lets say you want to create a user in a database -->
<!-- How would you go about creating that function? -->

````md magic-move
```ts
function createUser(db: Database, user: User) {

}
```

<!-- Let's start with our core logic -->

```ts
function createUser(db: Database, user: User) {
  return db.create(user)
}
```

```ts
function createUser(db: Database, user: User) {
  if (user != null) {
    return db.create(user)
  } else {
    throw new Error("user is undefined")
  }
}
```

<!-- That would work, but now lets check that the user isn't undefined -->

```ts
function createUser(db: Database, user: User) {
  if (user != null) {
    if (db.isConnected()) {
      return db.create(user)
    } else {
      throw new Error("database not connected")
    }
  } else {
    throw new Error("user is undefined")
  }
}
```

<!-- And what if we want to make sure the user's email is unique -->

```ts
function createUser(db: Database, user: User) {
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

````

<br />

<v-click>
  <p>What a mess!</p>
</v-click>