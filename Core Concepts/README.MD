# Core Concepts in ReactJs
## Components
Components are the building blocks of any React application. A React component is a JavaScript class or function that optionally accepts inputs i.e. properties(props) and returns a React element that describes how a section of the UI should appear.
### Function vs Class Components.
There are two types of components in React: Function components and Class components.
#### Function Components
Function components are the simplest form of React components. They are JavaScript functions that accept props as an argument and return a React element.
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```
#### Class Components
Class components are ES6 classes that extend from React.Component. They have a render method that returns a React element.
```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```
### Props
Props are short for properties. They are inputs to a React component. Props are passed to components via HTML attributes and are read-only.
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
const element = <Welcome name="John" />;
```
### State
State is a built-in feature in React components that allows components to keep track of changing data. State is mutable and can be updated using the `setState` method.
```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }
  render() {
    return (
      <div>
        <p>{this.state.count}</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Increment
        </button>
      </div>
    );
  }
}
```
### Lifecycle Methods
Lifecycle methods are special methods that are called at specific points in a component's lifecycle. They allow you to run code at certain points in the component's lifecycle, such as when the component is mounted or updated.
```jsx
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = { date: new Date() };
  }
  componentDidMount() {
    this.timerID = setInterval(() => this.tick(), 1000);
  }
  componentWillUnmount() {
    clearInterval(this.timerID);
  }
  tick() {
    this.setState({ date: new Date() });
  }
  render() {
    return <p>{this.state.date.toLocaleTimeString()}</p>;
  }
}
```
### Hooks
Hooks are a new addition in React 16.8 that allow you to use state and other React features in function components. They let you use state and other React features without writing a class.
```jsx
import React, { useState } from 'react';
function Counter() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>{count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```
### Context
Context provides a way to pass data through the component tree without having to pass props down manually at every level. It is designed to share data that can be considered "global" for a tree of React components.
```jsx
const ThemeContext = React.createContext('light');
class App extends
React.Component {
  render() {
    return (
      <ThemeContext.Provider value="dark">
        <Toolbar />
      </ThemeContext.Provider>
    );
  }
}
function Toolbar() {
  return (
    <ThemeContext.Consumer>
      {value => <Button theme={value} />}
    </ThemeContext.Consumer>
  );
}
```
### Refs
Refs provide a way to access DOM nodes or React elements created in the render method. They are useful for managing focus, text selection, or media playback.
```jsx
class MyComponent
extends React.Component {
  constructor(props) {
    super(props);
    this.myRef = React.createRef();
  }
  render() {
    return <div ref={this.myRef} />;
  }
}
```
### Error Boundaries
Error boundaries are React components that catch JavaScript errors anywhere in their child component tree and log those errors, display a fallback UI, or recover from the error.
```jsx
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }
  static getDerivedStateFromError(error) {
    return { hasError: true };
  }
  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong.</h1>;
    }
    return this.props.children;
  }
}
```
### Portals
Portals provide a way to render children into a DOM node that exists outside the DOM hierarchy of the parent component. They are useful for scenarios such as modals, tooltips, and popovers.
```jsx
class Modal extends React.Component {
  render() {
    return ReactDOM.createPortal(
      this.props.children,
      document.getElementById('modal-root')
    );
  }
}
```
### Fragments
Fragments let you group a list of children without adding extra nodes to the DOM. They are useful when you need to return multiple elements from a component's render method.
```jsx
function Table() {
  return (
    <>
      <tr>
        <td>John</td>
        <td>Doe</td>
      </tr>
      <tr>
        <td>Jane</td>
        <td>Doe</td>
      </tr>
    </>
  );
}
```
### Higher-Order Components
Higher-order components are functions that take a component and return a new component with additional functionality. They are a common pattern in React for code reuse, logic abstraction, and state manipulation.
```jsx
function withData(WrappedComponent) {
  return class extends React.Component {
    render() {
      return <WrappedComponent data={data} />;
    }
  };
}
```
### Render Props
Render props is a technique for sharing code between React components using a prop whose value is a function. It allows you to pass a function as a prop to a component and have that component render the result of calling that function.
```jsx
class Mouse extends React.Component {
  constructor(props) {
    super(props);
    this.state = { x: 0, y: 0 };
  }
  handleMouseMove = event => {
    this.setState({
      x: event.clientX,
      y: event.clientY
    });
  };
  render() {
    return (
      <div onMouseMove={this.handleMouseMove}>
        {this.props.render(this.state)}
      </div>
    );
  }
}
```
### Lazy Loading
Lazy loading is a technique for delaying the loading of non-essential resources at the time of the initial page load. It can help improve the performance of your React application by reducing the initial load time.
```jsx
const MyComponent = React.lazy(() => import('./MyComponent'));
```
### Suspense
Suspense is a new feature in React that allows components to suspend rendering while they load data asynchronously. It is useful for handling loading states and displaying fallback UIs while waiting for data to load.
```jsx
const resource = createResource();
function ProfilePage() {
  return (
    <Suspense fallback={<Spinner />}>
      <ProfileDetails />
    </Suspense>
  );
}
```
### Concurrent Mode
Concurrent Mode is a new experimental feature in React that allows components to render asynchronously. It is designed to improve the responsiveness of your React application by breaking up work into smaller chunks and prioritizing high-priority updates.
```jsx
ReactDOM.createRoot(document.getElementById('root')).render(<App />);
```
### Server-Side Rendering
Server-Side Rendering (SSR) is a technique for rendering React components on the server and sending the generated HTML to the client. It can help improve the performance of your React application by reducing the time to first paint and improving SEO.
```jsx
ReactDOMServer.renderToString(<App />);
```
### Static Site Generation
Static Site Generation (SSG) is a technique for generating static HTML files for your React application at build time. It can help improve the performance of your React application by pre-rendering pages and serving them as static files.
```jsx
export async function getStaticProps() {
  const data = await fetchData();
  return { props: { data } };
}
```
### Progressive Web Apps
Progressive Web Apps (PWAs) are web applications that provide a native app-like experience on the web. They can be installed on a user's device and work offline, push notifications, and access device features.
```jsx
const swUrl = `${process.env.PUBLIC_URL}/service-worker.js`;
serviceWorker.register(swUrl);
```
### Testing
Testing is an essential part of building React applications. React provides utilities for testing components, hooks, and asynchronous code to ensure your application works as expected.
```jsx
import { render, screen } from '@testing-library/react';
test('renders learn react link', () => {
  render(<App />);
  const linkElement = screen.getByText(/learn react/i);
  expect(linkElement).toBeInTheDocument();
});
```
### Deployment
Deploying a React application involves building your application for production and hosting it on a server or a cloud platform. There are various ways to deploy a React application, including static site hosting, serverless deployment, and containerized deployment.
```bash
npm run build
```
### Performance Optimization
Performance optimization is crucial for ensuring your React application runs smoothly and efficiently. Techniques such as code splitting, lazy loading, memoization, and server-side rendering can help improve the performance of your React application.
```jsx
const MyComponent = React.memo(() => <div>My Component</div>);
```
### Security
Security is a critical aspect of building React applications. It is essential to follow best practices for securing your React application, such as using HTTPS, avoiding cross-site scripting (XSS) attacks, and protecting sensitive data.
```jsx
const token = process.env.REACT_APP_API_TOKEN;
fetch('https://api.example.com/data', {
  headers: {
    Authorization: `Bearer ${token}`
  }
});
```
### Accessibility
Accessibility is an important consideration when building React applications. It is essential to ensure your application is accessible to users with disabilities by following best practices for keyboard navigation, screen reader support, and semantic HTML.
```jsx
<button aria-label="Close" onClick={handleClose}>
  <span aria-hidden="true">&times;</span>
</button>
```
### Internationalization
Internationalization (i18n) is the process of adapting your React application to different languages and regions. It is essential to provide support for multiple languages, date formats, and currencies to make your application accessible to a global audience.
```jsx
import { IntlProvider, FormattedMessage } from 'react-intl';
<IntlProvider locale="en" messages={messages}>
  <FormattedMessage id="greeting" />
</IntlProvider>
```
### State Management
State management is a critical aspect of building React applications. It is essential to manage the state of your application efficiently using tools such as React Context, Redux, MobX, or Recoil to ensure your application remains scalable and maintainable.
```jsx
const [state, dispatch] = useReducer(reducer, initialState);
```
### Routing
Routing is essential for building single-page applications with React. It allows you to navigate between different views or pages in your application and maintain the state of the UI. React Router is a popular library for handling routing in React applications.
```jsx
import { BrowserRouter as Router, Route, Link } from 'react-router-dom';
<Router>
  <Route path="/" component={Home} />
  <Route path="/about" component={About} />
</Router>
```
### Styling
Styling is an essential part of building React applications. There are various ways to style React components, including CSS-in-JS libraries, CSS modules, and inline styles. It is essential to choose a styling approach that suits your project requirements and team preferences.
```jsx
import styled from 'styled-components';
const Button = styled.button`
  background-color: #007bff;
  color: #fff;
`;
```
### Server-Side Rendering
Server-Side Rendering (SSR) is a technique for rendering React components on the server and sending the generated HTML to the client. It can help improve the performance of your React application by reducing the time to first paint and improving SEO.
```jsx
ReactDOMServer.renderToString(<App />);
```
### Static Site Generation
Static Site Generation (SSG) is a technique for generating static HTML files for your React application at build time. It can help improve the performance of your React application by pre-rendering pages and serving them as static files.
```jsx
export async function getStaticProps() {
  const data = await fetchData();
  return { props: { data } };
}
```
### Progressive Web Apps
Progressive Web Apps (PWAs) are web applications that provide a native app-like experience on the web. They can be installed on a user's device and work offline, push notifications, and access device features.
```jsx
const swUrl = `${process.env.PUBLIC_URL}/service-worker.js`;
serviceWorker.register(swUrl);
```
### Testing
Testing is an essential part of building React applications. React provides utilities for testing components, hooks, and asynchronous code to ensure your application works as expected.
```jsx
import { render, screen } from '@testing-library/react';
test('renders learn react link', () => {
  render(<App />);
  const linkElement = screen.getByText(/learn react/i);
  expect(linkElement).toBeInTheDocument();
});
```
### Deployment
Deploying a React application involves building your application for production and hosting it on a server or a cloud platform. There are various ways to deploy a React application, including static site hosting, serverless deployment, and containerized deployment.
```bash
npm run build
```
### Performance Optimization
Performance optimization is crucial for ensuring your React application runs smoothly and efficiently. Techniques such as code splitting, lazy loading, memoization, and server-side rendering can help improve the performance of your React application.
```jsx
const MyComponent = React.memo(() => <div>My Component</div>);
```
### Security
Security is a critical aspect of building React applications. It is essential to follow best practices for securing your React application, such as using HTTPS, avoiding cross-site scripting (XSS) attacks, and protecting sensitive data.
```jsx
const token = process.env.REACT_APP_API_TOKEN;
fetch('https://api.example.com/data', {
  headers: {
    Authorization: `Bearer ${token}`
  }
});
```
### Accessibility
Accessibility is an important consideration when building React applications. It is essential to ensure your application is accessible to users with disabilities by following best practices for keyboard navigation, screen reader support, and semantic HTML.
```jsx
<button aria-label="Close" onClick={handleClose}>
  <span aria-hidden="true">&times;</span>
</button>
```
