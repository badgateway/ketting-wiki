```typescript
/**
 * An action represents a hypermedia form submission or action.
 */
interface Action<T> {

  /**
   * Execute the action or submit the form.
   */
  submit(formData: T): Promise<State>;

}
```
