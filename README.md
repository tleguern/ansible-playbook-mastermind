# Ansible Playbook: Mastermind

An Ansible playbook solely dedicated to playing the game of [Mastermind](https://en.wikipedia.org/wiki/Mastermind_(board_game)), although a bit mixed with [Bulls and Cows](https://en.wikipedia.org/wiki/Bulls_and_Cows).

During the first run of the playbook a secret code composed of four coloured pegs will be generated randomly and stored by Ansible as a fact.
Users have 12 turns to find the correct combination, submitting guesses through the `--extra-vars` command line option.

The game will display the result as a number of “bulls” (number of correctly guessed colours and positions) or “cows” (number of correctly guessed colours but incorrect positions).

The algorithm is not yet perfect as the number of “cows“ can be incorrectly detected, giving hints to the player about the missing colours.

## Example of play

First the game is initialized:

```sh
$ ansible-playbook mastermind.yml 
PLAY [localhost] ***************************************************************

TASK [Select the colour of four pegs.] *****************************************
included: ansible-mastermind/peg-colour.yml for localhost
included: ansible-mastermind/peg-colour.yml for localhost
included: ansible-mastermind/peg-colour.yml for localhost
included: ansible-mastermind/peg-colour.yml for localhost

[...]

TASK [debug] *******************************************************************
ok: [localhost] => 
  msg: |-
      To play the game you have to run the playbook successively using the option --extra-var to define the guess variable. For example: --extra-var "guess=blue,black,yellow,red"

[...]

PLAY RECAP *********************************************************************
localhost: ok=13   changed=0    unreachable=0    failed=0    skipped=7    rescued=0    ignored=0   
```

The first guess is submitted:

```sh
$ ansible-playbook -e "guess=blue,black,yellow,red" mastermind.yml
PLAY [localhost] ***************************************************************

TASK [Select the colour of four pegs.] *****************************************
skipping: [localhost] => (item=0) 
skipping: [localhost] => (item=1) 
skipping: [localhost] => (item=2) 
skipping: [localhost] => (item=3) 

TASK [debug] *******************************************************************
skipping: [localhost]

TASK [set_fact] ****************************************************************
ok: [localhost]

TASK [assert] ******************************************************************
ok: [localhost]

TASK [assert] ******************************************************************
ok: [localhost]

TASK [include_tasks] ***********************************************************
included: ansible-mastermind/bull-or-cow.yml for localhost

[...]

TASK [Increase turn number.] ***************************************************
ok: [localhost]

TASK [debug] *******************************************************************
ok: [localhost] => 
  msg: 'Turn 1: 1 bulls and 1 cows'

TASK [include_tasks] ***********************************************************
skipping: [localhost]

PLAY RECAP *********************************************************************
localhost                  : ok=18   changed=0    unreachable=0    failed=0    skipped=3    rescued=0    ignored=0   
```

## License

ISC

## Contributing

Either send [send GitHub pull requests](https://github.com/tleguern/ansible-playbook-mastermind) or [send patches on SourceHut](https://lists.sr.ht/~tleguern/misc).

## Author Information

Tristan Le Guern <tleguern@bouledef.eu>
