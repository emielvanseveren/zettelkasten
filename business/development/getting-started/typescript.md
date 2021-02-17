---
Title: Typescript
Description:
Date: 05-05-2020
Tags: #javascript, #typescript
References:
Editor: markdown
---

# Typescript 

## Array
Get distinct items in array. It works because a **Set** cannot have duplicate objects 
```typescript
Array.from(new Set(yourArray.map((item: any) => item.id)))
```