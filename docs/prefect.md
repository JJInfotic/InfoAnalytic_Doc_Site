# **Welcome to Prefect**

Prefect enables you to build and observe resilient data workflows so that you can understand, react to, and recover from unexpected changes. It's the easiest way to transform any Python function into a unit of work that can be observed and orchestrated. Just bring your Python code, sprinkle in a few decorators, and go!

With Prefect you gain:

<ul class="ul-line-height-compress" style="columns: 2">
    <li> <a href="/concepts/schedules"> scheduling </a> </li>
    <li> <a href="/concepts/tasks/#task-arguments"> retries </a> </li>
    <li> <a href="/concepts/logs/"> logging </a> </li>
    <li> <a href="/concepts/tasks/#caching"> caching</a> </li>
    <li> <a href="/concepts/task-runners/#task-runners"> async</a> </li>
    <li> <a href="/cloud/automations/"> notifications</a> </li>
    <li> <a href="/cloud/overview/"> observability</a> </li>
</ul>


<figure markdown>
![screenshot of Cloud UI timeline view with menu](img/ui/flow-run-page.png)
<figcaption>Prefect UI</figcaption>
</figure>

#### New to Prefect?
If you're ready to dive in and learn Prefect, check out the Prefect [concepts](/concepts/index/) and try some [tutorials](/tutorial/) to see how they work in action.

For deeper dives on specific topics, explore our [guides](guides/index/) for common use-cases. <div style="height: 10px"></div>

[Concepts](/concepts){ .md-button .main-button--secondary .full } [Tutorials](/tutorial/){ .md-button .md-button--primary .main-button--primary .full }  [Guides](guides){ .md-button .main-button--secondary .full }

<div style="height: 10px"></div>
<p>Or, read on for a quick sample of Prefect.</p>
---

## Quick Start: Hello Prefect

Install Prefect with 

<div class="terminal">
```bash
pip install -U prefect
```
</div>

See the [install guide](/getting-started/installation/) for more detailed instructions.

### Run a basic flow

Import `flow` and decorate your Python function using the [`@flow`][prefect.flows.flow] decorator.

```python hl_lines="1 3"
from prefect import flow

@flow
def my_favorite_function():
    print("What is your favorite number?")
    return 42

print(my_favorite_function())
```

Thats it! Your function is now a flow. Run the code as you normally would, and you'll see its execution via the Prefect logs:

<div class="terminal">
```bash
$ python hello_prefect.py
15:27:42.543 | INFO    | prefect.engine - Created flow run 'olive-poodle' for flow 'my-favorite-function'
15:27:42.543 | INFO    | Flow run 'olive-poodle' - Using task runner 'ConcurrentTaskRunner'
What is your favorite number?
15:27:42.652 | INFO    | Flow run 'olive-poodle' - Finished in state Completed()
42
```
</div>

Prefect automatically persists all executions of your flow along with useful metadata such as start time, end time, and state. This is just the beginning, so keep exploring to learn how to add retries, notifications, scheduling and much more!

## Next Steps
To learn more, try our [tutorials](/tutorials) and [guides](/guides), or go deeper with [Prefect concepts](/concepts).

!!! tip "Need help?"
    Get your questions answered with a Prefect product advocate by [Booking A Rubber Duck](https://calendly.com/prefect-experts/prefect-product-advocates?utm_campaign=prefect_docs_cloud&utm_content=prefect_docs&utm_medium=docs&utm_source=dpcs)!