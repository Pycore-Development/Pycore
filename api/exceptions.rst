.. currentmodule:: pycore

Exceptions
==========

Exception Hierarchy
-------------------

.. exception_hierarchy::

    - :exc:`Exception`
        - :exc:`pycoreException`
            - :exc:`ClientException`
                - :exc:`InvalidData`
                - :exc:`InvalidArgument`
                - :exc:`LoginFailure`
                - :exc:`ConnectionClosed`
                - :exc:`PrivilegedIntentsRequired`
                - :exc:`InteractionResponded`
            - :exc:`NoMoreItems`
            - :exc:`GatewayNotFound`
            - :exc:`HTTPException`
                - :exc:`Forbidden`
                - :exc:`NotFound`
                - :exc:`pycoreServerError`
            - :exc:`ApplicationCommandError`
                - :exc:`CheckFailure`
                - :exc:`ApplicationCommandInvokeError`
            - :exc:`ExtensionError`
                - :exc:`ExtensionAlreadyLoaded`
                - :exc:`ExtensionNotLoaded`
                - :exc:`NoEntryPointError`
                - :exc:`ExtensionFailed`
                - :exc:`ExtensionNotFound`
            - :exc:`sinks.SinkException`
                - :exc:`sinks.RecordingException`
                - :exc:`sinks.WaveSinkError`
                - :exc:`sinks.MP3SinkError`
                - :exc:`sinks.MP4SinkError`
                - :exc:`sinks.M4ASinkError`
                - :exc:`sinks.MKVSinkError`
                - :exc:`sinks.MKASinkError`
                - :exc:`sinks.OGGSinkError`

Objects
-------

The following exceptions are thrown by the library.

.. autoexception:: pycoreException

.. autoexception:: ClientException

.. autoexception:: LoginFailure

.. autoexception:: NoMoreItems

.. autoexception:: HTTPException
    :members:

.. autoexception:: Forbidden

.. autoexception:: NotFound

.. autoexception:: pycoreServerError

.. autoexception:: InvalidData

.. autoexception:: InvalidArgument

.. autoexception:: GatewayNotFound

.. autoexception:: ConnectionClosed

.. autoexception:: PrivilegedIntentsRequired

.. autoexception:: InteractionResponded

.. autoexception:: pycore.opus.OpusError

.. autoexception:: pycore.opus.OpusNotLoaded

.. autoexception:: pycore.ApplicationCommandError
    :members:

.. autoexception:: pycore.CheckFailure
    :members:

.. autoexception:: pycore.ApplicationCommandInvokeError
    :members:

.. autoexception:: pycore.ExtensionError
    :members:

.. autoexception:: pycore.ExtensionAlreadyLoaded
    :members:

.. autoexception:: pycore.ExtensionNotLoaded
    :members:

.. autoexception:: pycore.NoEntryPointError
    :members:

.. autoexception:: pycore.ExtensionFailed
    :members:

.. autoexception:: pycore.ExtensionNotFound
    :members:

.. autoexception:: pycore.sinks.SinkException

.. autoexception:: pycore.sinks.RecordingException

.. autoexception:: pycore.sinks.WaveSinkError

.. autoexception:: pycore.sinks.MP3SinkError

.. autoexception:: pycore.sinks.MP4SinkError

.. autoexception:: pycore.sinks.M4ASinkError

.. autoexception:: pycore.sinks.MKVSinkError

.. autoexception:: pycore.sinks.MKASinkError

.. autoexception:: pycore.sinks.OGGSinkError
