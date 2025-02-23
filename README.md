# Next.js Readme Guide 🚀

## Table of Contents:
1. [Next.js and SEO](#nextjs-and-seo) 🔍
2. [Routing in Next.js](#routing-in-nextjs) 🔗
3. [Dynamic Routes](#dynamic-routes) 🌐
4. [Meta Tags](#meta-tags) 🏷️
5. [Data Fetching](#data-fetching) 📡
6. [Client-Side and Server-Side Code](#client-side-and-server-side-code) 🖥️

---

## Next.js and SEO 🔍
Next.js helps improve SEO (Search Engine Optimization) by rendering pages on the server side before sending them to the browser. This means search engines can easily index your pages and improve visibility, helping your site rank better! 📈

---

## Routing in Next.js 🔗

To create a new page, follow these steps:

1. **Create a new page**:
   - Inside the `app` folder, create a folder for your page (e.g., `app/f`).
   - Then, create a `page.jsx` file in that folder.
   - The route will be automatically created based on the folder structure.

Example:
```bash
app/
    page.jsx  # This will be accessible as "/f"
```

2. **Linking pages with `<Link>`**:
   You can use the `<Link>` component to navigate between pages in Next.js.

Example:
```jsx
<Link href=""><button>Prev 🔙</button></Link>
```

---

## Layout in Next.js 🏗️
- The `layout.jsx` file is used to define components that are shared across all pages, such as headers, footers, or navigation. 
- This file will wrap all pages inside the folder and apply the layout structure to them.

Example:
```bash
app/
    layout.jsx
    page.jsx
```

The `layout.jsx` file will repeat on all pages under the folder, giving your app a consistent structure. 🛠️

---

## Dynamic Routes 🌐
You can create dynamic routes by using square brackets `[]`. This allows you to handle dynamic parameters in your URL.

Example:
```bash
app/
  [id]/  # This will handle routes like "/1", "/2", etc.
    page.jsx
```
This makes your app more flexible by handling different content with a single route! 📄

---

## Meta Tags 🏷️
To set meta tags (like the title of the page), use the `metadata` object in your page or layout file.

Example:
```jsx
export const metadata = {
  title: "Articles Page 📚",  // The title shown in the browser tab
};
```
Setting a title helps search engines understand the content of your page! 📍

---

## Data Fetching 📡

To fetch data from an API, use an asynchronous function to fetch data before rendering the page.

### Server-Side Data Fetching 🌍:
In the `page.jsx` file:
```jsx
export default async function PostsPage() {
  const response = await fetch("https://jsonplaceholder.typicode.com/todos/1");
  const todo = await response.json();

  return (
    <div>
      <h1>Posts Page 📝</h1>
      <h2>{todo.title}</h2>
    </div>
  );
}
```

### Client-Side Data Fetching 📲:
If you need to use client-side fetching (in a component), use the `useState` and `useEffect` hooks.

Example:
```jsx
"use client";
import { useState, useEffect } from "react";

export default function Todo() {
  const [todo, setTodo] = useState({});

  useEffect(() => {
    async function fetchTodo() {
      const response = await fetch("https://jsonplaceholder.typicode.com/todos/1");
      const result = await response.json();
      setTodo(result);
    }
    fetchTodo();
  }, []);

  return (
    <div>
      <h1>{todo.title}</h1>
    </div>
  );
}
```
In this example:
- We use `useEffect` to fetch data when the component is mounted 🏗️.
- We store the data in `todo` using `useState` 📥.

---

## Client-Side and Server-Side Code 🖥️

- **Server-Side Code**: Use `async` functions directly in the `page.jsx` to fetch data.
- **Client-Side Code**: Use `"use client"` at the top of the file, and inside the component, use `useState` and `useEffect` to handle data fetching.
