# ⚛️ React Interview Questions — Complete Guide (2025–2026)

> **100+ must-know questions** | No answers — test yourself!
> Covers: Fundamentals → Hooks → State Management → Performance → Advanced Patterns → React 19 → Testing → Scenario-Based

---

## 📋 Table of Contents

1. [React Fundamentals](#1-react-fundamentals)
2. [JSX & Components](#2-jsx--components)
3. [Props & State](#3-props--state)
4. [React Hooks](#4-react-hooks)
5. [Lifecycle Methods](#5-lifecycle-methods)
6. [Event Handling & Forms](#6-event-handling--forms)
7. [State Management](#7-state-management)
8. [Performance Optimization](#8-performance-optimization)
9. [Routing](#9-routing)
10. [Advanced Patterns](#10-advanced-patterns)
11. [Server-Side Rendering & Next.js](#11-server-side-rendering--nextjs)
12. [React 19 — Latest Features](#12-react-19--latest-features)
13. [Testing](#13-testing)
14. [Scenario-Based & System Design](#14-scenario-based--system-design)

---

## 1. React Fundamentals

1. What is React? What are its key features?
2. What is the Virtual DOM? How does it work?
3. How does React's Virtual DOM differ from the real DOM?
4. What is the Diffing Algorithm in React?
5. What is Reconciliation in React?
6. What is React Fiber?
7. What is the difference between React and React DOM?
8. What are the advantages and disadvantages of using React?
9. How does React differ from Angular and Vue.js?
10. What is the difference between a library and a framework? Which one is React?
11. What is unidirectional data flow in React?
12. What is the significance of `key` prop in lists?
13. What is React StrictMode and why should you use it?
14. What is the difference between `createElement` and JSX?
15. What are Synthetic Events in React?

---

## 2. JSX & Components

16. What is JSX? Why do developers prefer it over plain JavaScript?
17. How does JSX get transformed to JavaScript? What is Babel's role?
18. What are the rules of JSX?
19. What is the difference between a Functional Component and a Class Component?
20. Why are functional components preferred over class components in modern React?
21. What are Presentational (Dumb) and Container (Smart) components?
22. What are Pure Components? How do they differ from regular components?
23. What is `React.memo()`? When should you use it?
24. What are Fragments in React? Why are they useful?
25. What are React Portals? When would you use them?
26. What is the difference between controlled and uncontrolled components?
27. What is a Higher-Order Component (HOC)? Give an example.
28. What are Render Props? How do they compare to HOCs?
29. What is the purpose of `defaultProps` and how do you define them?
30. How do you conditionally render components in React?

---

## 3. Props & State

31. What are props in React? How do they differ from state?
32. Can a child component modify its props? Why or why not?
33. What is prop drilling? What problems does it cause?
34. How do you pass data from a child component to a parent component?
35. What is state in React? How does it differ from props?
36. How does `setState()` work in class components? Is it synchronous or asynchronous?
37. What is the purpose of the callback function in `setState()`?
38. How do you lift state up in React? When should you do it?
39. What is derived state? What are the risks of using it?
40. What is the difference between state and derived state?
41. What is immutability and why is it important in React state management?
42. How do you update nested state objects correctly in React?
43. What is the difference between `null`, `undefined`, and missing props in React?

---

## 4. React Hooks

44. What are React Hooks? Why were they introduced?
45. What are the Rules of Hooks? Why must they be followed?
46. What is `useState()`? How does it work?
47. What is `useEffect()`? What is it used for?
48. What is the difference between `useEffect` and `useLayoutEffect`?
49. How does the dependency array in `useEffect` work? What happens if it is empty?
50. How do you clean up side effects in `useEffect`?
51. What is `useContext()`? How does it work?
52. What is `useReducer()`? When should you use it instead of `useState()`?
53. What is `useCallback()`? When should you use it?
54. What is `useMemo()`? When should you use it?
55. What is the difference between `useMemo` and `useCallback`?
56. What is `useRef()`? When would you use it over state?
57. What is `useImperativeHandle()`? When is it useful?
58. What is `useTransition()`? What problem does it solve?
59. What is `useDeferredValue()`? How is it different from `useTransition`?
60. What is `useId()`? What is it used for?
61. What are custom hooks? How do you create one?
62. How do you share logic between components using custom hooks?
63. Why can't hooks be called inside loops, conditions, or nested functions?
64. What is `useDebugValue()`?
65. What happens if you call `useState` setter multiple times in one event handler?

---

## 5. Lifecycle Methods

66. What are the lifecycle phases of a React class component?
67. What is `componentDidMount()`? What is its functional component equivalent?
68. What is `componentDidUpdate()`? When is it called?
69. What is `componentWillUnmount()`? What is its functional component equivalent?
70. What is `shouldComponentUpdate()`? How does it improve performance?
71. What is `getDerivedStateFromProps()`? When would you use it?
72. What is `getSnapshotBeforeUpdate()`?
73. How do you handle errors in React components? What is `componentDidCatch()`?
74. What are Error Boundaries? How do you implement one?
75. Can Error Boundaries catch errors in event handlers? Why or why not?

---

## 6. Event Handling & Forms

76. How does event handling in React differ from vanilla HTML?
77. What are Synthetic Events in React? Why does React use them?
78. What is the difference between controlled and uncontrolled form components?
79. How do you prevent the default behavior of an event in React?
80. How do you handle form submissions in React?
81. How do you implement form validation in React?
82. What is `event.persist()` and when was it needed?
83. How do you handle multiple input fields in a single state object?

---

## 7. State Management

84. What is Context API? How does it work?
85. When should you use Context API vs. a state management library like Redux?
86. What are the performance pitfalls of React Context? How do you mitigate them?
87. What is Redux? What are its core principles?
88. What are Actions, Reducers, and the Store in Redux?
89. What is the difference between Redux and Context API?
90. What is Redux Toolkit? How does it simplify Redux?
91. What are Redux middleware? What does `redux-thunk` do?
92. What is `redux-saga`? How does it differ from `redux-thunk`?
93. What is Zustand? How does it compare to Redux?
94. What is Recoil? What problem does it solve?
95. What is React Query (TanStack Query)? Why use it for server state?
96. What is the difference between client state and server state?
97. How do you decide which state management solution to use in a project?

---

## 8. Performance Optimization

98. What are common causes of unnecessary re-renders in React?
99. How does `React.memo()` prevent unnecessary re-renders?
100. What is memoization in React? When should you use it?
101. How do `useCallback` and `useMemo` help with performance?
102. What is code splitting? How do you implement it in React?
103. How does `React.lazy()` work with `Suspense`?
104. What is lazy loading? How does it improve performance?
105. What is virtualization (windowing)? Which libraries implement it for React?
106. How would you implement infinite scrolling in React?
107. What is the React Profiler? How do you use it to debug performance?
108. What are React DevTools and how do they help?
109. How do you prevent unnecessary re-renders when passing objects/arrays as props?
110. What is the "key" anti-pattern of using array index as keys in lists?
111. How does tree shaking work in React projects?
112. How do you reduce the bundle size of a React application?

---

## 9. Routing

113. What is React Router? What problem does it solve?
114. What is the difference between `BrowserRouter` and `HashRouter`?
115. What is the difference between `<Link>` and `<a>` in React Router?
116. How do you implement dynamic routing with URL parameters in React Router?
117. What are nested routes in React Router v6?
118. How do you implement protected/private routes in React?
119. How do you programmatically navigate in React Router v6?
120. What is the `useNavigate` hook? How does it replace `useHistory`?
121. What are `useParams`, `useLocation`, and `useSearchParams` hooks?
122. How do you handle 404 pages in React Router?

---

## 10. Advanced Patterns

123. What is the Compound Component pattern? Give an example use case.
124. What is the Provider pattern in React?
125. What is the Observer pattern and how is it used in React?
126. What is the difference between composition and inheritance in React?
127. What is a Slot pattern in React?
128. What are Render Props and when would you use them today?
129. What is `forwardRef`? When do you need it?
130. What is `React.cloneElement()` and when is it used?
131. What is the difference between `React.Children.map` and `Array.map`?
132. What is tree shaking and how does it apply to React component libraries?
133. How do you implement a debounce or throttle in React?
134. How do you handle race conditions in `useEffect` data fetching?
135. What are memory leaks in React? How do you prevent them?
136. What is Flux architecture? How does Redux differ from it?

---

## 11. Server-Side Rendering & Next.js

137. What is Server-Side Rendering (SSR)? What are its advantages and disadvantages?
138. What is Client-Side Rendering (CSR)? How does it differ from SSR?
139. What is Static Site Generation (SSG)?
140. What is Incremental Static Regeneration (ISR)?
141. What is hydration in React? What causes hydration mismatches?
142. What are React Server Components (RSC)?
143. What is the difference between Server Components and Client Components?
144. How do you decide when to use a Server Component vs. a Client Component?
145. What is the `"use client"` directive in React?
146. What is Next.js? What are its key features?
147. What is the difference between the Pages Router and App Router in Next.js?
148. How does data fetching work in the Next.js App Router?
149. What is streaming in React and Next.js?

---

## 12. React 19 — Latest Features

150. What are the major new features introduced in React 19?
151. What is the React Compiler (React Forget)? How does it change how we write code?
152. How does the React Compiler handle memoization automatically?
153. Do you still need `useMemo`, `useCallback`, and `React.memo` with the React Compiler?
154. What is the Actions API in React 19?
155. What is `useActionState()`? What problem does it solve?
156. What is `useOptimistic()`? How do you use it for optimistic UI updates?
157. What is `useFormStatus()`? When is it useful?
158. What is the `use()` hook in React 19? How does it differ from `await`?
159. How have Server Actions changed form handling in React 19?
160. What is the `"use server"` directive?
161. What changes were made to `Suspense` in React 19?
162. What breaking changes were introduced in React 19 (e.g., removal of `ReactDOM.render()`)?
163. Is React 19 backward compatible with React 18?
164. What is `Activity` in React 19.2?
165. How does concurrent rendering work in React 19?

---

## 13. Testing

166. What testing frameworks are commonly used with React?
167. What is React Testing Library? What is its philosophy?
168. What is the difference between unit testing, integration testing, and end-to-end testing?
169. How do you test a component that uses `useState`?
170. How do you test a component that makes API calls?
171. What is mocking in React testing? How do you mock a module in Jest?
172. What is `jest.fn()`? How do you test callbacks/props with it?
173. What is snapshot testing? When is it useful and when is it not?
174. How do you test React hooks using React Testing Library?
175. What is Cypress? How does it differ from Jest?
176. What is `act()` in React testing? Why is it needed?
177. How do you test for accessibility in React components?
178. What is the `screen` object in React Testing Library?

---

## 14. Scenario-Based & System Design

179. Your React application is rendering slowly. Walk through how you would diagnose and fix the performance issues.
180. A component is re-rendering unnecessarily due to function and object references. How would you fix it?
181. You have deeply nested components and prop drilling is becoming unmanageable. What approach would you take?
182. You need to fetch and display data efficiently while keeping the UI responsive. How would you design this?
183. Your application has a large bundle size affecting load time. What strategies would you use to reduce it?
184. You are building a large-scale dashboard where frequent state updates are causing UI lag. How do you optimize rendering?
185. How would you implement a real-time feature (like live chat or stock prices) in React?
186. You need to implement a form with complex validation, dynamic fields, and performance requirements. What solution would you use?
187. How would you handle authentication (login/logout, protected routes) in a React SPA?
188. How would you implement dark mode across an entire React application?
189. Implement a component that efficiently renders 10,000 list items without crashing the browser.
190. Your `useEffect` is causing an infinite loop. How do you debug and fix it?
191. How would you manage state in a large-scale React application with multiple teams?
192. You need to build a reusable component library. What considerations and patterns would you use?
193. How would you migrate a large legacy class component codebase to functional components with hooks?
194. What architectural decisions would you make for a React app that needs to support SSR, SEO, and high performance?

---

## 🔑 Quick Reference — Key Terms

| Term | One-line Definition |
|---|---|
| Virtual DOM | In-memory JS representation of the real DOM for efficient updates |
| Reconciliation | React's process of comparing old and new virtual DOM to find minimal changes |
| React Fiber | Reimplemented React core enabling incremental rendering and prioritization |
| JSX | JavaScript syntax extension that looks like HTML, compiled by Babel |
| Hook | Function letting functional components use state and lifecycle features |
| Controlled Component | Component whose form input value is driven by React state |
| HOC | Function that takes a component and returns an enhanced component |
| Memoization | Caching computed results to avoid redundant recalculation |
| Code Splitting | Breaking bundle into chunks loaded on demand, reducing initial load |
| SSR | Rendering React on the server and sending HTML to the client |
| RSC | Server Components — render on server with zero client-side JS |
| Hydration | React attaching event listeners to server-rendered HTML on the client |
| React Compiler | Build-time optimizer in React 19 that auto-memoizes components |
| useTransition | Hook to mark non-urgent state updates, keeping UI responsive |
| Actions API | React 19 pattern for handling async form operations with built-in states |

---

*Compiled from: GeeksforGeeks, InterviewBit, GreatFrontEnd, CodeForGeek, NamasteDev, DEV Community, Medium, and official React docs — April 2026*

*Good luck with your interview! ⚛️🚀*
