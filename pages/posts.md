---
type: page
title: Thoughts
date: 2020-01-04
description: Thoughts on life, work, and everything else.
---

# Thoughts

import { getPagesUnderRoute } from "nextra/context";
import Link from "next/link";

export function BlogIndex({ more = "Read more" }) {
  return getPagesUnderRoute("/posts").sort((a, b) => {
    return new Date(b.frontMatter.date) > new Date(a.frontMatter.date) ? 1 : -1;
  }).map((page) => {
    // Alias `<a>` to avoid it being replaced by MDX components.
    const A = "a";
    const H3 = 'h3'
    return (
      <div key={page.route} className="mb-10">
        <Link href={page.route}>
          <A style={{ color: "inherit", textDecoration: "none" }} className="post-link block font-semibold mt-8 text-2xl flex">
            <H3 className="flex-1 m-0 post-title">{page.meta?.title || page.frontMatter?.title || page.name}</H3>
            <time className="opacity-50 text-sm date">{page.frontMatter.date}</time>
          </A>
        </Link>
      </div>
    );
  });
}

<BlogIndex/>
