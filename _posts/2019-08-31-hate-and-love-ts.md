---
layout: page
title: "My relationship with typescript"
description: >
  Typescript is my bane
tag: [blog]
---

If I had a counter for all the times typescript has saved me from making a careless mistake, the number would pale in comparison to the number stackoverflow pages I looked up trying to figure out how to fix my TS error while my app was recompiling.

For those who are unfamiliar with Typescript, is a superset of javascript that is hard-typed. Typescript requires that you state the types of all variables and objects which are typically stated optionally. For example, here's how I would state the types of my props in a typescript react app:

~~~
import * as React from "react";

User = {
  email: string;
  dob: string;
  active: boolean;
}

interface IProps {
  first_name: string;
  patientId: string;
  numberOfChildren: number;
  user: User;
}
~~~

This is great since it helps you get ahead of some common errors you may have had to debug only after you launched your app. Typescript will throw you an error for using an untyped variable, using a variable that can possibly be undefined, stating a variable but never using it, and likely many more errors that I have yet to run into!

I completely understand the validity of using typescript as a means to sniff out bad code as early as possible and it has definitely made me a more thoughtful dev.

As it stands today, I am still on the fence on the cost-benefit of using typescript in the long run as I have spent more time that I would've liked compiling. This will also likely get better in the future (Should write another blog post on how to decrease the compiling time when running react apps).
