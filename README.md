# SA-recorder
Sound Activated Recorder on headless, passwordless RPI

# Description
SA-recorder is an always-on recording solution. It actively listens to audio channels on a connected soundcard and starts recording once a certain loudness threshold is exceeded.

# Not yet implemented
- SA-recorder should apply some basic audio processing to the recordings (normalization etc)
- SA-recorder should manage all files (+backups). Possibly connected to a NAS
- SA-recorder should produce logs locally
- SA-recorder should send a status report via mail on a selected interval (daily)

# Setup Pi with ssh login (headless)
See SETUP.md for step-by-step setup of a raspberry Pi for use with SA-recorder.
