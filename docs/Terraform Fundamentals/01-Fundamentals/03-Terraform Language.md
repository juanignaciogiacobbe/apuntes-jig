# Terraform Language

> [!NOTE] Terraform Language
> It's main purpose is to declare resources. This represents infrastructure objects. 
> All the different features are present to accommodate more flexible and convenient resource definition.


![](../img/Pasted%20image%2020240925092354.png)

- **Blocks** are containers for objects like resources.
- **Arguments** assign a value to a name.
- **Expressions** represent a value.


> [!NOTE] File Extension
> Plain text files with the `.tf` file extension are where code in Terraform language is stored.
> You can also use a json variant of the language which uses the `.tf.json` file extension.


> [!NOTE] Text Encoding
> These plain text files must use UTF-8 encoding and usually use Unix-style line endings(LF), though it can also use Windows-style line endings(CRLF) as well.


> [!NOTE] Directories and Modules
> Modules are a collection of `.tf` and/or `.tf.json` files kept together in a directory.
> A module consists of only the top-level config files in the directory. A nested directory is treated as a separate module and may not be automatically included.


> [!NOTE] Root Module
> Terraform configuration consists of a root module and a few child modules. The root module is the working directory where Terraform is invoked.

## Override Files

![](../img/Pasted%20image%2020240925094128.png)

## Config Syntax

![](../img/Pasted%20image%2020240925095027.png)

> [!NOTE] Identifiers
> Things like argument names, block type names, resources, input variables, and etc.


> [!NOTE] Comments
> `#` begins a single-line comment.
> `//` also begins a single-line comment.
> `/*` and `*/` are start and end delimiters for a comment that might span over multiple lines.


## JSON Config Syntax

![](../img/Pasted%20image%2020240925095507.png)