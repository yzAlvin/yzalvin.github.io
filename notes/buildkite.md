Buildkite Agent
a small, reliable and cross-platform build runner.
runs automated builds on your own infrastructure.
main responsibilities:
* polling buildkite.com for work
* running build jobs
* reporting back the status code
* output log
* uploading job's artifacts

The agent polls Buildkite's agent API over HTTPS.
Agents can run across any number of machines and networks.

The agent registers itself with Buildkite, and once registered it's placed into your organisation's agents pool. The agent periodically polls Buildkite looking for new work.

Buildkite agents are small, reliable and cross-platform build runners that run automated builds. Buildkite never accesses your code, and does not run any agents, so you need to install and run agents on your own infrastructure. You can do this on you local development machine, an existing CI machine, or a new server.

Every agent comes with a config.



Buildkite is a vendor/tool that handles CI/CD
Computer installs buildkite-agent -> that computer can now receive jobs from some server on buildkites side
Company provides agents to buildkite, big server (HQ) provided by buildkite

Master/Slave architecture
Master computer tells slave computers what to do.

steps run in parallel until -wait

What do you want in your pipeline?
the stuff you want to do everytime you push your code

lint test build push

CloudFormation is a way to spin up AWS resources

can create pipeline through website UI
can use pipe from myob-ops



