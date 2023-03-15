# http-40x-status
Very good presentation of HTTP 40x errors

    +-----------------------
    | RESOURCE EXISTS ? (if private it is often checked AFTER auth check)
    +-----------------------
       |       |
    NO |       v YES
       v      +-----------------------
      404     | IS LOGGED-IN ? (authenticated, aka user session)
      or      +-----------------------
      401        |              |
      403     NO |              | YES
      3xx        v              v
              401            +-----------------------
          (404 no reveal)       | CAN ACCESS RESOURCE ? (permission, authorized, ...)
              or             +-----------------------
             redirect          |            |
             to login       NO |            | YES
                               |            |
                               v            v
                               403          OK 200, redirect, ...
                      (or 404: no reveal)
                      (or 404: resource does not exist if private)
                      (or 3xx: redirection)
