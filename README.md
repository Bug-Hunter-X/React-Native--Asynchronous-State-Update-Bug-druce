# React Native Asynchronous State Update Bug

This repository demonstrates a common but subtle bug in React Native related to asynchronous state updates. The bug occurs when an asynchronous operation (like a network request) modifies component state, but the component renders before the state is fully updated. This can lead to unexpected behavior, such as undefined values or errors.

## Bug Description

The `bug.js` file contains a React Native component that fetches data from an API. The problem lies in how the `setData` function is used inside the `useEffect` hook. Because the fetch operation is asynchronous, the component might render before `setData` finishes, resulting in an attempt to access `data.someValue` when `data` is still `null`.

## Solution

The `bugSolution.js` demonstrates a fix using the optional second argument in `useEffect` for cleanup and the `data` object's existence check. 