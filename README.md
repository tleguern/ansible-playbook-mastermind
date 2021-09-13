# Ansible Playbook: Mastermind

This project is attempt to bring the board game of of [Mastermind](https://en.wikipedia.org/wiki/Mastermind_(board_game)) (although a bit mixed with [Bulls and Cows](https://en.wikipedia.org/wiki/Bulls_and_Cows)) to Ansible.

The goal is to find a secret combination of four coloured pegs in a given number of turns (here twelve) by submitting guesses and analysing the answers.
The game will display the result as a number of “bulls” (number of correctly guessed colours and positions) or “cows” (number of correctly guessed colours but incorrect positions).

At the end of each turn a summary of past guesses is displayed like this:

```
TASK [debug] *******************************************************************
ok: [localhost] =>
  msg: |-
    Turn 1: |  red   |  red   |  red   |  red   |
    Turn 2: |  red   |  blue  |  blue  |  blue  |
    Turn 3: |  red   |  blue  |  blue  | black  |
    Turn 4: |  red   |  blue  | black  |  blue  |
    ----
    4 bulls and 0 cows
```

## How to play

The following packages are necessary:

- ansible

Simply run the following command:

```sh
$ ansible-playbook mastermind.yml
...
```

## License

ISC

## Contributing

Either send [send GitHub pull requests](https://github.com/tleguern/ansible-playbook-mastermind) or [send patches on SourceHut](https://lists.sr.ht/~tleguern/misc).

## Author Information

Tristan Le Guern <tleguern@bouledef.eu>
