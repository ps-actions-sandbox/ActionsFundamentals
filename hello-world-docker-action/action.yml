name: 'Hello World Docker Action'
description: 'Say hello to a user or the world.'
inputs:
  who-to-greet:
    description: 'Who to greet'
    required: true
    default: 'world'
outputs:
  time:
    description: 'The time we said hello.'
runs:
  using: 'docker'
  image: 'Dockerfile'
  args:
    - ${{ inputs.who-to-greet }}
