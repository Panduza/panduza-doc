---
title: "platform_error"
description: ""
weight: 1
icon: "error"
---

Here are the rules for the error management inside the platform

The file `src\platform\error.rs` provides the Error class for the platform. This error stores the file and the line of the error.

Platform provides 2 macros to help declaring platform errors.

```rust
// return a platform error object
use crate::platform_error;
// return a platform error object inside an Err result
use crate::platform_error_result;
```

Two other result types are defined for common cases

```rust
// For async task end result
use crate::platform::TaskResult;
// For generic task functions that just return OK on success
use crate::platform::FunctionResult;
```

Each function of the platform must return at some point an Error platform.
This allow platform top functions to manage the proper error management and display.
