TypeScript-এ interface এবং type প্রায় একই রকম কাজ করতে পারে, তবে কিছু গুরুত্বপূর্ণ পার্থক্য আছে। নিচে পার্থক্যগুলো দেওয়া হলো:

✅ ১. Extending (বাড়ানো):
interface:

একাধিক interface কে extend করা যায় (multiple inheritance):

interface A { a: string; }
interface B { b: number; }
interface C extends A, B { c: boolean; }

type:
একাধিক টাইপকে extend করতে হলে & (intersection) ব্যবহার করতে হয়:
type A = { a: string };
type B = { b: number };
type C = A & B & { c: boolean };

✅ ২. Declaration Merging (ঘোষণা একত্রিত হওয়া):
interface:

একই নামে একাধিক interface ঘোষণা করলে TypeScript নিজে থেকেই তাদের merge করে।

Edit
interface Person { name: string; }
interface Person { age: number; }

// Person = { name: string; age: number }

type:
একবার ঘোষণা করলে আবার একই নামে ঘোষণা করা যায় না (redeclaration error):

type Person = { name: string };
type Person = { age: number }; // ❌ Error

✅ ৩. Primitive টাইপ ও Tuple এর জন্য:
type দিয়ে primitive, union, intersection, tuple টাইপ তৈরি করা যায়:

type ID = string | number;
type Point = [number, number];
interface শুধু object টাইপের জন্য ব্যবহৃত হয় — primitive বা tuple এর জন্য নয়।

✅ ৪. কোথায় কোনটা ব্যবহার করবো?
সাধারণতঃ object এর structure define করতে interface ব্যবহার করা হয়।

যদি union, tuple, বা complex type composition দরকার হয়, তাহলে type ভালো।

🔍 উদাহরণস্বরূপ:

interface User {
  name: string;
  age: number;
}

type Status = "active" | "inactive";
type Coordinates = [number, number];
