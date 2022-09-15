# Learn Scrypto Episode 2 :microscope: A Peek Under the Hood :dna:

Picking up where we left off in episode 1 let's dig a little deeper and take a look under the hood for a minute to better understand what was created for us in our generated blueprint!

We will look at how to find more of the options and capabilities that we get from the Scrypto libraries and Radix engine. Then make our way through some other example blueprints and identify reusable patterns. In the end hopefully it will feel a bit more comfortable to compose your own custom blueprints.

## :brain: What you will Learn

1. How to find and work with built in scrypto features
2. How to utilize example blueprints
3. How to begin composing your own blueprints

> Bonus - The process behind understanding what a piece of code is doing and how to figure it out, potentially without even knowing a particular language or library or framework or api... you see where this is leading. We are expected to know so much as developers the way to really thrive is to learn how to quickly find answers without driving yourself crazy. **Key takeaway: the process is the important part of this lesson.**

### Step 1. Clone the scrypto-examples repository

In the location of your choice run

`git clone git@github.com:TheDevPath/scrypto-examples-ep2.git`

This will create a local copy of the repository that we can mangle and break and investigate to get a better idea what is going on under the hood. This is a fork of the official repository which you can find [here](https://github.com/radixdlt/scrypto-examples)

Open the scrypto-examples-ep2 directory in visual studio code as the workspace directory.

> **NOTE!** Be sure this is the top level directory for your VSCode workspace so that the rust-analyzer plugin will work correctly.

Navigate your terminal or powershell to -> `cd core/hello-world`

Now we can install our dependencies by running `cargo build`

> **NOTE** If you are familiar with node you can draw paralell between
> `package.json` = `cargo.toml` and `npm install` = `cargo build`

Now we have a project we can deploy and interact with via the `resim` radix engine simulator.

First up let's find out take a look at the hello world project we did in the first episode and find out what the ResourceBuilder looks like along with Bucket, Vault and some new items not seen just yet.

We can do this a couple ways:

1. Using our IDE to inspect the code brought in with our cargo crates
2. Find the package documentation - which is [here](https://radixdlt.github.io/radixdlt-scrypto/scrypto/index.html)

To get started open up `core/hello-world/src/lib.rs` this file is our Hello blueprint!

O

Bucket and Vault will look ordinary enough if you've worked in other languages with a type system and we will look at how to see what these custom types and others that are provided in scypto give us.

But what's with the :: well in rust this is a way to interact with namespaces and ResourceBuilder is a public struct we can access from the Scrypto Crate namespace. ie if you were to write it all the way out it would look like `scrypto::resource::ResourceBuilder`

Notice in this line `let my_bucket: Bucket = ResourceBuilder::new_fungible()` there is a type of Bucket being infered then the :: allows us to access the ResourceBuilder struct and call the new_fungible() function.

Then there's this `-> ComponentAddress` in the instantiation function the arrow indicates the return type of our instantiate function which is a custom type of ComponentAddress

Ok so let's take a stroll through the process I use to find these answers. I'll show you how to figure out what things are in the example blueprints and how you can go about beginning to compose your own custom blueprint logic.

### Step 2. Utilize Example Blueprints

The reason I set this project up using the examples repository rather than just generating a new project with the Scrypto CLI tool is so that we can learn the first phase of utilizing new tech.

:jigsaw: **Following patterns** can help you produce demonstratable results faster, build confidence and ultimately lead to the greater understanding needed to compose your own logic from scratch with a lot less headache.

Next let's open up `core/hello-nft/src/lib.rs`

We can quickly see similar elements to our Hello bluprint and also check out a couple new items here.

### Step 3. Compose Your Own Blueprints

This is where coding gets really fun, once you get comfortable composing your own logic you get to be creative and launch :rocket: those amazing ideas you come up with!

> ### Useful Docs Links
>
> scrypto crate docs -
> https://radixdlt.github.io/radixdlt-scrypto/scrypto/index.html
>
> radix_engine crate docs -
> https://radixdlt.github.io/radixdlt-scrypto/radix_engine/index.html
>
> sbor crate docs - https://radixdlt.github.io/radixdlt-scrypto/sbor/index.html
>
> Create a Basic Resource - https://radixdlt.github.io/radixdlt-scrypto/sbor/index.html
>
> Half-hour to learn Rust - https://fasterthanli.me/articles/a-half-hour-to-learn-rust
>
> The Rust Reference - https://doc.rust-lang.org/nightly/reference/introduction.html

### Key Scrypto Terms To Learn

> To Give Examples that may be more familiar at a high level the following are roughly the same:

- Scrypto Component
- Ethereum Smart Contract
- Cloud Functions

  _Based on the following perspective:_

> They all expose a public address which you can access to execute computation on the network.
>
> You pay a fee for the computation required to run your function.

- **Package** - a collection of blueprints that can be deployed to the radix network **hasAddress**
- **Blueprint!** - as the name implies this is your set of instructions your code **notAddressable**
- **Component** - a component is the stateful intantiated instance of a blueprint! **hasAddress**

- **Account** - Components instantiated from a special Account blueprint!

- **Resources** - Special Asset data types in Scrypto
- **Vault** - permanent resource container
- **Bucket** - temporary resource container
