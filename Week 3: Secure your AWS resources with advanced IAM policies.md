

## **This is what I have for you this week.**

Implementing Identity and Access Management (IAM) policies is a crucial aspect of securing AWS resources, enabling you to enforce the principle of least privilege and maintain granular control over access permissions. By leveraging IAM policies, you can define precise permissions for Users, User Groups, Roles, and Resources, ensuring that only authorized entities can perform specific actions on your AWS resources. This approach provides flexibility and scalability while minimizing security risks, allowing you to achieve a robust and compliant security posture in your AWS environment.

AWS, policies are defined using JSON (JavaScript Object Notation) code, which serves as a declarative configuration to instruct or communicate with AWS services. Two types of policies exist: Managed Policies and Custom Policies.

Managed Policies are predefined, built, and updated by AWS, making them immutable and non-editable. These policies are globally available and cannot be deleted. They provide a set of predefined permissions and access controls for AWS services.

Custom Policies, on the other hand, are user-defined policies that can be created, edited, copied, and deleted. These policies allow for fine-grained access control and permissions tailored to specific users, groups, or resources. Custom Policies can be attached to IAM users, groups, or roles, and can also be used to define resource-based policies.

I will be discussing on:

1. Json
2. Types of policies 
3. Creating of policies 
4. Policy structure
5. Policy generator
6. Policy simulator

Json: JavaScript Object Notation.

How does Json works? I will give a basic explanation on how to read a Json code.

Firstly, let me inform you about different types of brackets.

We have curly bracket { }, square bracket [ ], angle bracket < > and normal bracket.

Curly bracket depict an object while square bracket depict an Array. Calm down it is technical for you right I got you covered. Please go through the line again you will understand.


Example of Json code:

```
'{"name":"John", "age":30, "car":null}'
```

If you noticed this has a curly bracket which is an object telling us John is a name they are both coated, name is key 🔑 while John is a value, what it's means is that Json is about key and a value.

Age is a key 🔑 while 30 is a value, note number or figure is not coated just exactly in my example.

Car is a key 🔑 as I explained because we can have different types of cars but in this example is empty that's why it's written in null, note null doesn’t come with coated just like john.


Square bracket depict an array, check below for example.

```
'"Car": ["Ford", "BMW", "Fiat"]'
```

Arrays are like listing types of cars with square bracket, that's the function of [ ].

Now, let's talk about types of policies:

1. Managed Based policy (AWS)
2. Custom based policy (Customized)

Let me break it down:

Managed Based Policy (similar to AWS Policy):

- Pre-defined policy templates or frameworks.
- Standardized and widely adopted.
- Typically based on industry best practices or regulatory requirements.
- Easy to implement and manage
- Examples: AWS IAM policies, NIST frameworks


Custom Policy (similar to Customize Policy): 

- Unique, tailored policies created for specific needs
- Not based on pre-defined templates or frameworks
- Often require custom implementation and management
- May address specific business requirements or risks
- Examples: Custom security policies, company-specific compliance policies.


Let's move to creating of policy now that we know Json and type of policy.

Let me ask a technical question: 

> If we are creating policy, is it a Managed or Custom policy?

Tell me the answer. 

Custom policy. Correct! 

You guess right. Good of you, I know you are brilliant ☺.

Let's keep it going. We are going more technical now feel refresh and relax you will get my explanation if you follow me judiciously. 


Let's create and explain policy. Yes ☺ 


```
{
       "Version": "2012-10-17", 
       "Statement":  [
		{
                  "Sid": "Statement1",
		  "Effect": "Deny",
		  "Action": ['iam:changepassword'],
		  "Resource": ["*"]
 		},          
	]

}

```
This is a Structure Policy.

Let me explain this code with the basic knowledge of Json.

Version is depicting the when the version is created, it's is optional in Json code but the best practice is that it can be add it.


"Version" line is a statement single line of code while "Statement" is multiple lines of statement which includes arrays, please check very well.

Let's divide in "Statement"; "Sid" is means "Statement ID" which open opportunity of creating new Statement SID and different code. 

"Effect" give 2 options which "Allow" or "Deny". 

"Action" is a the code to tell what function should be carried out, for the example; to interpret the code it means you are denied to change your password. That's the literal meaning. 

Now, you can successfully read and interpret a Json code.

⁉Assignment, I will be waiting for your answer in the comment section.

```
{
       "Version": "2012-10-17", 
       "Statement":  [
		{
                  "Sid": "Statement1",
		  "Effect": "Allow",
		  "Action": ['s3:getobject'],
		  "Resource": ["*"]
 		},          
	]

}
```

Note Value is not case sensitivity.

If you want to [learn more](https://docs.aws.amazon.com)
🤗 Thank you for reading my little article for week 4.🤭

Give me your thoughts concerning my write up ✍ ✍ ✍ or recommendation.

My special regards goes to: 
Jamiu Olatunji Bakre
Cloud Engineer
