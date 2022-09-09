## Learn Scrypto Episode 2 - A Peek Under the Hood

Picking up where we left off in episode 1 let's dig a little deeper and take a look under the hood for a minute to better understand what was created for us in our generated blueprint! and learn how to find more options and capabilities that we get from the scrypto libraries and radix engine.

### What you will Learn

1. How to find and work with built in scrypto features
2. How to clone example blueprints and how to utilize them
3. How to begin composing your own blueprints

> Bonus - The process behind understanding what a piece of code is doing and how to figure it out, potentially without even knowing a particular language or library or framework or api... you see where this is leading. We are expected to know so much as developers the only way to really thrive is to learn how to quickly find the answers without driving yourself crazy. **Key takeaway the process is the important part of this lesson.**

> ## Step 1. Clone the scrypto-examples repository

In the location of your choice run

`git clone git@github.com:TheDevPath/scrypto-examples-ep2.git`

This will create a local copy of the repositry that we can mangle and break and investigate to get a better idea what is going on under the hood. This is a fork of the official repository which you can find [here](https://github.com/radixdlt/scrypto-examples)

Navigate to your terminal or powershell to -> `cd core/hello-world`

First lets find out what this ResourceBuilder is along with Bucket, Vault and some new items not seen just yet.

Bucket and Vault will look ordinary enough if you've worked in other languages with a type system and we will look at how to see what these custom types and others that are provided in scypto give us.

But what's with the :: well in rust this is a way to interact with namespaces and ResourceBuilder is a namespace we can acces in the Scrypto library we get from the Scrypto Cargo package.

notice in this line `let my_bucket: Bucket = ResourceBuilder::new_fungible()` there is already a type of Bucket being infered then the :: allows us to access the ResourceBuilder namespace and call the new_fungible() function.

And then there's this `-> ComponentAddress` in the instantiation function the arrow indicates the return type of our instantiate function which is a custom type of ComponentAddress

Ok so let's take a stroll through the process I used to find these answers. I'll show you how to figure out what things are in the example blueprints and how you can go about beginning to compose your own custom blueprint logic.

### Key Scrypto Terms To Learn

- Package: a collection of blueprints that can be deployed to the radix network **hasAddress**
- Blueprint! as the name implies this is your set of instructions your code **notAddressable**
- Component a component is the stateful intantiated instance of a blueprint! **hasAddress**

- Accounts Components instantiated from a special Account blueprint!

- Transaction Manifest

- Resources special data type in scrypto
- Vault : permanent resource container
- Bucket : temporary resource container
- Badges / Proofs
