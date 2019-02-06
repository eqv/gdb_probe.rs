gdb_probe
=======

You love `ipdb.set_trace()` in python  or `binding.pry` in ruby? You are sad that rust doesn't ofer the same comfort?
_gdb_probe_ is here to safe the day! With a simple call, it suspends the current process, spawns a new terminal and
attaches gdb.

How to use
--------

add `"gdb_probe="0.1"` to your Cargo.toml

```rust
extern crate gdb_probe;
use gdb_probe::gdb_probe;

fn main() {
    println!("Hello, world!");
    let x = 3+4;
    gdb_probe(); //spawns a new terminal (urxvt) with gdb attached at this position.
}
```

Known Caveats
-------
*Warning* If the target process dies before the debugger can attach, sometimes init is debugged instead. In that case forcefully
terminating the debugger causes a reboot.

Depends on urxvt as a terminal.
