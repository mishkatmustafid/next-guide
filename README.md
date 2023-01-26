# An Absolute Beginners Guide to Next.js

- How to bootstrap a React application with Nextjs
- and, how Nextjs can help you build production-grade React application

Next.js has a tone of features but in this video I'm only going to be covering the main ones you need to get started. After watching this video, I encourage you to go the Next.js documentation to see all the available features.

Next.js can be used to build static websites, along with server-rendered applications. In this guide I'm going to be showing you how you can implement both of these rendering strategies, so you can decide which one best suits your application.

**Bootstrap the application**

I'm going to be using TypeScript so I can show off some of the awesome TypeScript features that Next.js comes with for the TypeScript users, but you can follow along with JavaScript, even if you're not familiar with TypeScript.

```
npx create-next-app
# or
yarn create next-app

# with typescript
yarn create next-app my-app --typescript
```

**Create pages**

**\_app & \_document**

[https://nextjs.org/docs/advanced-features/custom-app](https://nextjs.org/docs/advanced-features/custom-app)

[https://nextjs.org/docs/advanced-features/custom-document](https://nextjs.org/docs/advanced-features/custom-document)

**Rendering strategies**

Static-site generation - Fastest

- Gets run at build time

```jsx
// Run at build time
export async function getStaticProps() {
  // Call an external API endpoint to get posts
  const res = await fetch("https://.../posts");
  const posts = await res.json();

  // By returning { props: { posts } }, the Blog component
  // will receive `posts` as a prop at build time
  return {
    props: {
      posts,
    },
  };
}

// Run at build time
export async function getStaticPaths() {
  // Call an external API endpoint to get posts
  const res = await fetch("https://.../posts");
  const posts = await res.json();

  // Get the paths we want to pre-render based on posts
  const paths = posts.map((post) => ({
    params: { id: post.id },
  }));

  // We'll pre-render only these paths at build time.
  // { fallback: false } means other routes should 404.
  return { paths, fallback: false };
}
```

Server-side rendering

```jsx
// This gets called on every request
export async function getServerSideProps() {
  // Fetch data from external API
  const res = await fetch(`https://.../data`);
  const data = await res.json();

  // Pass data to the page via props
  return { props: { data } };
}
```

**Routing**

[https://nextjs.org/docs/routing/introduction](https://nextjs.org/docs/routing/introduction)

**Styling**

[https://nextjs.org/docs/basic-features/built-in-css-support](https://nextjs.org/docs/basic-features/built-in-css-support)

**Environment variables**

[https://nextjs.org/docs/basic-features/environment-variables#loading-environment-variables](https://nextjs.org/docs/basic-features/environment-variables#loading-environment-variables)

**Router**

```jsx
import { useRouter } from "next/router";
```

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.

This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `pages/index.tsx`. The page auto-updates as you edit the file.

[API routes](https://nextjs.org/docs/api-routes/introduction) can be accessed on [http://localhost:3000/api/hello](http://localhost:3000/api/hello). This endpoint can be edited in `pages/api/hello.ts`.

The `pages/api` directory is mapped to `/api/*`. Files in this directory are treated as [API routes](https://nextjs.org/docs/api-routes/introduction) instead of React pages.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!
