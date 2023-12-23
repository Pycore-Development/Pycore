.. currentmodule:: pycore

Voice Related
=============

Objects
-------

.. attributetable:: VoiceClient

.. autoclass:: VoiceClient()
    :members:
    :exclude-members: connect, on_voice_state_update, on_voice_server_update

.. attributetable:: VoiceProtocol

.. autoclass:: VoiceProtocol
    :members:

.. attributetable:: AudioSource

.. autoclass:: AudioSource
    :members:

.. attributetable:: PCMAudio

.. autoclass:: PCMAudio
    :members:

.. attributetable:: FFmpegAudio

.. autoclass:: FFmpegAudio
    :members:

.. attributetable:: FFmpegPCMAudio

.. autoclass:: FFmpegPCMAudio
    :members:

.. attributetable:: FFmpegOpusAudio

.. autoclass:: FFmpegOpusAudio
    :members:

.. attributetable:: PCMVolumeTransformer

.. autoclass:: PCMVolumeTransformer
    :members:

Opus Library
------------

.. autofunction:: pycore.opus.load_opus

.. autofunction:: pycore.opus.is_loaded
