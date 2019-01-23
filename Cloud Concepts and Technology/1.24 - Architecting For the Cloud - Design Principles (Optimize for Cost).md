# 1.24 - Architecting For the Cloud - Design Principles (Optimize for Cost)

In this note we'll look at ways you can use AWS to leverage economies of scale to reduce your costs. See the [Cost Optimization with AWS](https://d0.awsstatic.com/whitepapers/Cost_Optimization_with_AWS.pdf) whitepaper for more info.

## Right Sizing

AWS offers a mind-boggling number of resource types and configurations for each of their different services. Bearing cost in mind when considering them is important. In some cases, the cheapest suitable instance might be the right call. In others, having fewer, larger, instances might work out to be more cost-efficient. A similar principle applies to storage options: **pick the right instance(s) for your needs**.

Also, remember that cost optimization is an **iterative process**. Just as you would monitor and tag your application NFRs, make sure to monitor your costs and continuously evaluate your solution.

AWS provides tools to help identify cost-saving opportunities. To make these these tools' outcomes easy to interpret, you should define and implement a tagging policy for your AWS resources. That implementation should be part of your build processed and automated appropriately, using tools like AWS Elastic Beanstalk or AWS OpsWorks, or even AWS Config.

## Elasticity

Another way to reduce costs is to take advantage of the platform's elasticity.  There are 3 main ways to do this.

* **Enable Auto Scaling** - Enable auto-scaling for as many EC2 instances as possible, to ensure that you can both scale up when needed, and scale down when you don't need the capacity to minimise costs.
* **Turn off non-production workloads when not in use**
* **Replace EC2 workloads with managed services** - Many AWS services either don't require you to make any capacity decisions (e.g. such as ELB, Amazon CloudFront, Amazon SQS, Amazon Kinesis Firehose, AWS Lambda, Amazon SES, Amazon CloudSearch, or Amazon EFS), or make it very easy to modify it (DynamoDB, RDS, ES). Take advantage of these services to reduce the amount of idle capacity you have.

## Take Advantage of Purchasing Options

In addition to on-demand instance pricing, Amazon offers a number of other ways to purchase compute capacity that can potentiall reduce spending.

### Reserved Instances

Reserved instance purchases essentially allow you to make a 3-5 year contract with Amazon in exchange for a significantly discounted hourly rate on the instances you reserve.

While this can be very cost-effective, its imperative to ensure you've sufficiently benchmarked your production applications before you purchase capacity. Otherwise, you risk overpaying for underused instances.

Technically, there is no difference between On-Demand and Reserved EC2 instances; the only difference is in how they are priced.

### Spot Instances

For workloads where you do not need consistent compute capacity and your work can tolerate interruption, it is worth considering using spot instances.

Spot instances are essentially unused EC2 instances. Their pricing fluctuates, and reflects both the long-term and short-term demand for their compute power. Your spot instance will run whenever your maximum price per hour exceeds the current Spot price. As you can imagine, these have the capability to significantly reduce costs.

Finally, by combining spot instances with On-Demand and Reserved instance pricing, you can also supplement a predictable minimum capacity with *opportunistic* access to additional compute resources. This can be an effective way to improve throughput or application performance.