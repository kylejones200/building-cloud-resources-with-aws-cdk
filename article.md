# Building cloud resources with AWS CDK How I use CDK to simplify and streamline building cloud infrastructure
with constructs so I can focus more on architecture/design and less...

### Building cloud resources with AWS CDK
#### How I use CDK to simplify and streamline building cloud infrastructure with constructs so I can focus more on architecture/design and less on infrastructure
When building cloud infrastructure efficiently and consistently,
developers often face the challenge of juggling complex configurations
and infrastructure-as-code (IaC) solutions. AWS Cloud Development Kit
(CDK) simplifies and streamlines this process. At the heart of AWS CDK
is a concept known as "constructs", which are the building blocks for
cloud resources. These constructs provide developers with a higher-level
abstraction, allowing them to focus more on the architecture and less on
the nitty-gritty details of infrastructure setup.


<figcaption>Photo by <a
href="https://unsplash.com/@liamread?utm_source=medium&amp;utm_medium=referral"
class="markup--anchor markup--figure-anchor"
data-href="https://unsplash.com/@liamread?utm_source=medium&amp;utm_medium=referral"
rel="photo-creator noopener" target="_blank">Liam Read</a> on <a
href="https://unsplash.com?utm_source=medium&amp;utm_medium=referral"
class="markup--anchor markup--figure-anchor"
data-href="https://unsplash.com?utm_source=medium&amp;utm_medium=referral"
rel="photo-source noopener" target="_blank">Unsplash</a></figcaption>


### What are CDK Constructs and how are they helpful?
CDK constructs simplify creating and managing cloud resources by
offering reusable components. They encapsulate best practices and help
you set up servers, storage, and databases without defining each
configuration manually. Think of them as pre-configured templates, ready
to be used as pieces of your infrastructure puzzle. You can use these
constructs to declare and define a range of resources, such as an S3
bucket or an EC2 instance, without getting bogged down in how each
service should be set up.

The CDK has three levels of constructs: L1, L2, and L3.

L1 constructs are directly mapped to AWS CloudFormation resources.
Essentially, they give you access to the raw CloudFormation resource
definitions, giving you complete control over all the possible
configurations. This is great for those who need a lot of customization
or are already familiar with CloudFormation templates. However, for most
developers, starting with this level is like working from scratch,
you'll need to understand every aspect of the resource you're deploying.
It's flexible but not the most straightforward approach for everyday
use.

That's where L2 constructs come into play. L2 constructs are more
abstract than L1 and wrap together multiple CloudFormation resources.
Instead of configuring every last detail, L2 constructs provide sensible
defaults that work for most scenarios. For example, instead of defining
every attribute of an S3 bucket or an IAM policy, you can use an L2
construct that already knows the most commonly needed settings while
allowing you to tweak specific aspects if required. This approach speeds
up development significantly, making infrastructure creation less of a
chore and more of a creative process.

L3 constructs go this a step further by bundling together numerous L2
constructs to make more complicated cloud applications. These are
higher-level building elements designed to make full solutions more
accessible to implement. For example, you might use an L3 construct to
set up a whole backend service that includes a load balancer, EC2
instances, a database, and even the security configurations, all in one
go. By taking care of the integration between distinct components, L3
constructs allow you to focus on developing your application
architecture rather to worrying about how the underlying pieces go
together.

What makes CDK constructs especially powerful is their reusability and
extensibility. Once you've defined a construct, you can reuse it across
different parts of your infrastructure or various projects. This modular
approach makes your infrastructure easier to maintain, especially as it
grows in complexity. If you need to make changes, you only need to
modify the construct in one place, and the changes will apply wherever
the construct is used.

Developers can also extend existing constructs or create entirely new
ones. This means you can define and package your custom cloud resources
to fit your particular use case. It's a bit like building with LEGO
blocks, you have predefined pieces that work well together, but you can
also combine them in new ways to create something unique to your needs.

CDK constructs promote best practices by embedding security,
scalability, and resilience into the code. By using constructs, you
don't need to constantly worry about whether your S3 bucket is encrypted
or whether your VPC is configured securely. These best practices come
baked into the constructs themselves, reducing the risk of
misconfigurations. You still have control, but CDK makes it easier to
stay within the bounds of a good approach.

Another advantage of CDK constructs is that they're language-agnostic.
While CloudFormation relies on JSON or YAML templates, CDK lets you
define constructs using familiar programming languages like TypeScript,
Python, Java, and C#. This makes infrastructure-as-code much more
approachable for developers already comfortable with one of these
languages. You can integrate cloud resource management directly into
your development workflow, writing code that looks and feels like the
rest of your application.

Since constructs are defined programmatically, applying logic and
conditions in ways that aren't feasible with traditional CloudFormation
templates is also possible. For example, you could define a construct
that automatically chooses different configurations depending on the
environment (development, testing, production). You could also iterate
over lists of resources or dynamically generate names and
configurations, adding flexibility that simplifies large-scale
deployments.

Working with CDK constructs transforms the cloud infrastructure setup
from a tedious, manual task into a streamlined, programmatic process.
Whether you're a startup trying to set up a basic cloud architecture or
a large enterprise managing complex deployments, CDK constructs make
managing resources clearly and consistently easier.

### How to use the AWS Construct Library
Using AWS to build applications or infrastructure involves several
services and tools. Below is a simple introduction to key services like
EC2, S3, Lambda, and RDS, along with how to combine these services to
create an application or solution.

**1. EC2 (Elastic Compute Cloud)**

EC2 provides scalable virtual servers, allowing you to run various
operating systems and applications in the cloud.

**How to use**

- Log into the AWS console and navigate to EC2.
- Choose "Launch Instance" and select an AMI (Amazon Machine Image)
  based on your needs, configuring CPU, memory, and storage.
- Set up security groups, allowing specific IP addresses to access the
  instance or open necessary ports (like 80 or 443).
- Assign an elastic IP address to ensure a fixed IP address for the
  instance.
- Connect to the instance: use SSH to connect to Linux or RDP for
  Windows instances.

**Use cases**

This is useful for running web servers or databases and handling
long-running computation tasks.

**2. S3 (Simple Storage Service)**

S3 provides object storage, ideal for storing any data file type, like
images, videos, backups, and more.

**How to use**

- Log into the AWS console and navigate to S3.
- Create an S3 bucket to store your data files.
- Upload files: you can upload files through the console or use AWS CLI
  or SDK.

S3 allows you to control access with bucket policies, making files
public or accessible to specific users.

Enable versioning control can track changes to objects over time.

**Use cases**

This is useful for storing static resources such as images, videos, and
documents. You can also use S3 as backup storage or large data analysis.

**3. Lambda (Serverless Computing)**

Lambda is a serverless computing service that allows you to run code
without managing servers. Code is executed by triggering events, like an
S3 file upload or an API request.

How to use

- Log into the AWS console and navigate to Lambda.
- Create a Lambda function: choose a runtime (like Python, Node.js, or
  Java), and either upload your code or write it directly in the
  console.
- Set up triggers: Lambda functions can be triggered by S3, API
  Gateway, CloudWatch, and more.
- Set permissions: use IAM roles to control Lambda's access to other
  AWS services.
- Deploy**:** Lambda functions scale automatically and charge based on
  the number of executions.

**Use cases**

This is often used to build serverless APIs. It can also be used for
processing S3 file uploads (e.g., image processing, video conversion)
and running background tasks or automation.

**4. RDS (Relational Database Service)**

RDS provides managed relational databases such as MySQL, PostgreSQL, SQL
Server, and Oracle.

**How to use**

- Log into the AWS console and navigate to RDS.
- Create a database instance: Choose the engine and configure the
  instance type, storage, and backup settings.
- Set up VPC, subnets, and security groups for database
  security.
- Use the provided RDS endpoint to connect to the database.
- Set up automatic backups and monitoring.

**Use cases**

This is useful for hosting relational databases to support applications.
You can also use it for managing database clusters to ensure high
availability and disaster recovery.

### Related Stories
- [[Setting up AWS CDK for your
  projects](https://medium.com/@kylejones_47003/setting-up-aws-cdk-for-your-projects-713d1d518b9a)]
- [[Managing different environments for AWS CDK (Dev, Test,
  Prod)](https://medium.com/@kylejones_47003/managing-different-environments-for-aws-cdk-dev-test-prod-3ce6336bb7c0)]
- [[How AWS CDK turns code into CloudFormation
  Templates](https://medium.com/@kylejones_47003/how-aws-cdk-turns-code-into-cloudformation-templates-8f725301ef17)]
::::::::By [Kyle Jones](https://medium.com/@kyle-t-jones) on
[September 30, 2024](https://medium.com/p/7a8ee677e309).

[Canonical
link](https://medium.com/@kyle-t-jones/building-cloud-resources-with-aws-cdk-7a8ee677e309)

Exported from [Medium](https://medium.com) on November 10, 2025.
