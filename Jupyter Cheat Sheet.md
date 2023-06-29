# Jupyter Cheat Sheet

## Display documentation for commands

```python
<cmd>?
```

### Example

```python
import chipwhisperer as cw
cw.scope?

    Signature:
    cw.scope(
        scope_type: Optional[Type[Union[chipwhisperer.capture.scopes.OpenADC.OpenADC, chipwhisperer.capture.scopes.cwnano.CWNano]]] = None,
        name: Optional[str] = None,
        sn: Optional[str] = None,
        idProduct: Optional[int] = None,
        bitstream: Optional[str] = None,
        force: bool = False,
        prog_speed: int = 10000000,
        **kwargs,
    ) -> Union[chipwhisperer.capture.scopes.OpenADC.OpenADC, chipwhisperer.capture.scopes.cwnano.CWNano]
    Docstring:
    Create a scope object and connect to it.

    This function allows any type of scope to be created. By default, the
    object created is based on the attached hardware (OpenADC for
    CWLite/CW1200, CWNano for CWNano).
...
```

### Notes

Same info as `help()` function in Python

## Display source code for commands

```python
<cmd>??
```

### Example

```python
import chipwhisperer as cw
cw.scope??

    def capture_trace(scope : scopes.ScopeTypes, target : targets.TargetTypes, plaintext : bytearray,
        key : Optional[bytearray]=None, ack : bool=True, poll_done : bool=False,
        as_int : bool=False, always_send_key=False) -> Optional[Trace]:

        """Capture a trace, sending plaintext and key
        ...
        """

        import signal

        if key:
            target.set_key(key, ack=ack, always_send=always_send_key)

        scope.arm()

        if plaintext:
            target.simpleserial_write('p', plaintext)

        ...
```

## Search Module

```python
?module.*<search>*
```

### Example

```python
?cw.*target*

    cw.program_target
    cw.target
    cw.target_logger
    cw.targets
```

## Jupyter Quick Reference

```python
%quickref
```

## Plotting Command

```python
plot = cw.plot(<data>)
display(plot)
```

### Example

```python
trace_data = scope.get_last_trace()
plot = cw.plot(trace_data)
display(plot)
```

### Overlaying Plots

```python
# previously captured trace0 and trace1
plot = cw.plot(trace0) * cw.plot(trace1)
display(plot)
```