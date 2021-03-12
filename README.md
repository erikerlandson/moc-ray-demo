# moc-ray-demo

A demonstration of using the Ray distributed computing platform with Jupyter on Open Data Hub.

#### Prerequisites

Running Ray with Jupyter on Open Data Hub assumes you have a working Ray+ODH integration, as described in this
[ray-odh-demo](https://github.com/erikerlandson/ray-odh-demo).

The Open Data Hub running on the
[Massachussets Open Cloud](https://www.operate-first.cloud/users/support/)
currently supports Ray on ODH.

#### To run the test notebook:

This "smoke-test" notebook shows how to connect to a ray cluster from jupyter in ODH,
and run a basic computation.

1. Log into the ODH JupyterHub launcher. You should see a ray-enabled notebook image option such as `ray-ml-notebook`: choose this.
1. In the environment variable section, add `JUPYTER_PRELOAD_REPOS` and set to `https://github.com/erikerlandson/moc-ray-demo.git`
1. Launch your JupyterHub environment. As part of the startup process, the ODH JupyterHub launcher should also start up a Ray cluster.
1. In Jupyter, navigate to directory `moc-ray-demo.git/source` and open the "smoke-test" notebook.
1. Run the notebook cells to confirm that it connects to your ray cluster and operates correctly.
1. If the connection to the Ray cluster results in a timeout, wait a minute and re-try.

Caveat: The demo function in this test notebook reports the names of the ray cluster nodes it used to compute.
The Ray operator adaptively scales the clusters it is managing based on workload.
When running the demo function, it may not use all available nodes depending on how many were spun up at the time,
and how long it took to run its computations.
Repeatedly running the test frequently causes more nodes to report in the result.

#### Doing ML with Ray and Juptyter and Jupyter

I will be adding a demonstration of basic ML workloads, using ray and jupyter notebooks, to this section soon.

#### Caveats and Limitations

1. Ray support for Jupyter and ODH is currently experimental, and based on pre-release development versions of Ray 2.0
1. Currently a hard maximum of 5 Ray worker nodes is configured.
1. Ray nodes are configured for 1 CPU and 1 GiB of RAM.
