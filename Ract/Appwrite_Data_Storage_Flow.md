# Appwrite Environment Variables and Storage Guide

Think of Appwrite as a huge building.

Inside that building:

* One room stores users
* One room stores posts
* One room stores images
* One room stores files
* One room stores databases

Your `.env` variables are basically addresses telling your app:

> Which building?
>
> Which room?
>
> Which storage box?

---

# 1. VITE_APPWRITE_URL

```env
VITE_APPWRITE_URL=https://cloud.appwrite.io/v1
```

This is the BUILDING ADDRESS.

Your frontend asks:

> Where is the Appwrite server located?

Without this, your app does not know where to send requests.

Visualize:

```txt
Your React App
      ↓
https://cloud.appwrite.io/v1
      ↓
Appwrite Server
```

---

# 2. VITE_APPWRITE_PROJECT_ID

```env
VITE_APPWRITE_PROJECT_ID=abc123
```

Inside Appwrite, you can have many projects.

Example:

```txt
Project 1 → Blog Website
Project 2 → Chat App
Project 3 → Ecommerce
```

This ID tells:

> Use THIS project.

Visualize:

```txt
Appwrite Building
    ↓
Choose Project
    ↓
Your Blog App
```

---

# 3. VITE_APPWRITE_DATABASE_ID

```env
VITE_APPWRITE_DATABASE_ID=xyz456
```

Inside your project, databases exist.

A database is like a big cupboard storing data.

Example:

```txt
Database
   ↓
Posts
Users
Comments
```

This ID tells:

> Open this database cupboard.

---

# 4. VITE_APPWRITE_COLLECTION_ID

```env
VITE_APPWRITE_COLLECTION_ID=postcollection
```

Inside a database there are collections.

A collection is a group of similar documents.

Example:

```txt
Collection: Posts
--------------------------------
Post 1
Post 2
Post 3
```

Each post is called a document.

Example document:

```json
{
  "title": "My First Post",
  "content": "Hello world",
  "image": "image_file_id"
}
```

This collection ID tells:

> Store or read posts from THIS collection.

---

# 5. VITE_APPWRITE_BUCKET_ID

```env
VITE_APPWRITE_BUCKET_ID=imagesbucket
```

This is where images and files are stored.

A bucket is a storage room for files.

Visualize:

```txt
Bucket
   ↓
photo1.png
photo2.jpg
banner.webp
```

When a user uploads an image:

```txt
User uploads file
      ↓
Appwrite Bucket stores image
      ↓
Appwrite returns a unique file ID
```

Example:

```txt
fileId = "682hf72hd"
```

That file ID is usually saved inside a database document.

Example:

```json
{
  "title": "Nature",
  "image": "682hf72hd"
}
```

---

# Full Image Upload Flow

### Step 1: User Selects an Image

```txt
nature.jpg
```

### Step 2: Upload Image to Bucket

```js
const file = await storage.createFile(
  bucketId,
  ID.unique(),
  imageFile
)
```

Appwrite stores the image and returns:

```js
file.$id
```

Example:

```txt
abc999
```

### Step 3: Save File ID in Database

```js
databases.createDocument(...,{
   title: "My Blog",
   image: "abc999"
})
```

Now the database knows:

```txt
This post uses image abc999
```

---

# How the Image Comes Back

Later, when displaying the post:

Database returns:

```json
{
  "title": "My Blog",
  "image": "abc999"
}
```

Your app then asks:

> Appwrite, give me the image whose ID is abc999.

Example:

```js
storage.getFilePreview(bucketId, "abc999")
```

or

```js
storage.getFileView(bucketId, "abc999")
```

Appwrite returns an image URL.

Example:

```txt
https://cloud.appwrite.io/v1/storage/buckets/...
```

React displays the image:

```jsx
<img src={imageUrl} />
```

---

# Complete Flow Visualization

```txt
User uploads image
       ↓
Bucket stores image
       ↓
Bucket returns file ID
       ↓
Database saves file ID
       ↓
Later app reads database
       ↓
Gets file ID
       ↓
Requests image from bucket
       ↓
Gets image URL
       ↓
Image displayed on website
```

---

# Key Relationship

```txt
Database = Stores information
Bucket   = Stores actual image/file
```

The database does NOT store the image itself.

It only stores the image's file ID as a reference.
