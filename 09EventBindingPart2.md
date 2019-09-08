# Topic 9: Event Binding: Part 2

1. DOM event handling mechanism in Angular can be augmented to let the child send data to the parent. But there are many moving parts.
2. Like an HTML element, we like our child component expose its own custom events. Custom events, because these are emited at the behest of the child component.
3. Child exposes an instance of EventEmitter (make sure this class is imported from @angular/core package) with @Output() decorator. This instance is the custom event of the child component henceforth.
4. When something happens in the child, say a button click, the child uses this custom event instance and calls emit() method with data if required
5. As for the parent, this event is like any other DOM event. So, the parent is going to provide its own handler to handle this custom event exposed by the child.
6. In child, we use: `@Output() customEvent = new EventEmitter();` to expose a custom event
7. When child wants to send data to the parent: `this.customEvent.emit({...});`
8. Inside the parent template, the parent provides handler for this custom event as: `<app-child (customEvent)="parentHandler($event)"></app-child>`
9. `$event` is mandatory here if the parent wants to get the event args (same way as any DOM event)
10. Please note that, the parent has no compulsion to listen to the child events by providing the handler methods. It can choose to ignore the custom event.
11. Please refer to out-event-binding branch of <https://github.com/vivekanandpv/angular-event-binding>
