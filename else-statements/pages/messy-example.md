# Let's do an example

<!-- Lets say you want to create a user in a database -->
<!-- How would you go about creating that function? -->

Lets say you need to create a function to add a new user to the database

<v-click>

````md magic-move
```ts
function createUser(user: User): DatabaseData {
  if (db.isConnected()) {
    return db.create(user)
  } else {
    throw new Error("database not connected")
  }
}
```

<!-- That would work, but now lets check that the user isn't undefined -->

```ts
function createUser(user: User): DatabaseData {
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

````

</v-click>

<br />

<v-click>
  Messy, right?
</v-click>