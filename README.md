# Ansible Playbook: Mastermind

This project is attempt to bring the board game of of [Mastermind](https://en.wikipedia.org/wiki/Mastermind_(board_game)) (although a bit mixed with [Bulls and Cows](https://en.wikipedia.org/wiki/Bulls_and_Cows)) to Ansible.

The goal is to find a secret combination of four coloured pegs in a given number of turns (here twelve) by submitting guesses and analysing the answers.
The game will display the result as a number of “bulls” (number of correctly guessed colours and positions) or “cows” (number of correctly guessed colours but incorrect positions).
The algorithm is not yet perfect as the number of “cows“ can be incorrectly detected, giving hints to the player about the missing colours.

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
