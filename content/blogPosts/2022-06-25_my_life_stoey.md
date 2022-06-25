---
title: my life stoey
date: 2022-06-25T23:41:21.992Z
thumbnail: /static/img/827a88e7-c942-4e33-999d-f6b68e323a00-1.png
---
## 44##

## jacansnne

## One-sided & two-sided relationships

In Keystone it’s possible to define relationships from one, or both sides of the two lists you’re connecting. We refer to these as *one-sided*, and *two-sided* relationships:

### [](https://keystonejs.com/docs/guides/relationships#one-sided)One-sided

Our example above is one-sided: the `Post` list relates to the `User` list via the `authors` field. This kind of relationship will let us query for the `authors` of a post in our GraphQL API like so:

```
bxbcbcbcbcbcbbcbcbcb
```

### [](https://keystonejs.com/docs/guides/relationships#two-sided)Two-sided

If we can find all the `authors` of a post, we can also find all the posts written by a particular user. To do this we need to configure a two-sided relationship in our schema:

```

```

In the example above we added a `posts` field to the `User` list, and changed the `ref` config of the `authors` field to be `User.posts`.

In a two-sided relationship the `ref` config must be formatted as `<listName>.<fieldName>` and both sides must refer to each other.

Now that our relationship is two-sided we can query all the posts written by each user like so:

```javascript
const data   = maddd
dadadadd
addadad
```

**Things to keep in mind:**\
\
Two-sided relationships are declared in two places, but **there is only one relationship between both lists**.\
\
**Both fields share the same data**. If you change the author of a post, that post will no longer show up in the original author’s posts.

### [](https://keystonejs.com/docs/guides/relationships#self-referencing-relationships)Self-referencing relationships

Keystone also lets you define one, and two-sided **relationships that refer to the same list**. To make a *one-sided* Twitter style following relationship we do the following:

```

```

Or change this into a *two-sided* relationship to also access the followers of every user:

```

```

The only relationship configuration not currently supported is having a field reference itself, e.g. `friends: relationship({ ref: 'User.friends', many: true })`.

## [](https://keystonejs.com/docs/guides/relationships#establishing-cardinality)Establishing cardinality

*Cardinality* is a term used to describe how many items can exist on either side of a relationship. Each side can have either `one` or `many` related items. Since each relationship can have one and two sides, we have the following options available:

| Relationship type | One to one | One to many | Many to many |
| ----------------- | ---------- | ----------- | ------------ |
| One-sided         | ❌          | ✅           | ✅            |
| Two-sided         | ✅          | ✅           | ✅            |

Cardinality is defined through the `relationship` field’s `many` configuration option. It’s a boolean where:

* `false` = one
* `true` = many