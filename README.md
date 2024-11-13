# pynanit

    Python library for the unofficial Nanit API

This is a Python port of the API client in https://gitlab.com/adam.stanek/nanit.
It provides an async HTTP client using [aiohttp](https://docs.aiohttp.org).
I'm using it to integrate Nanit natively with Home Assistant.

## Usage

```
from pynanit import NanitClient
import aiohttp

credentials = ('user@domain.tld', 'password')

async with aiohttp.ClientSession() as session:
    client = NanitClient(session)
    mfa_token = await client.initiate_login(*credentials)
    mfa_code = input('Enter the MFA code from your email: ')
    login_result = await client.complete_login(*credentials, mfa_token=mfa_token, mfa_code=mfa_code)

    babies = await client.get_babies()
    baby_uid = babies['babies'][0]['uid']

    events = await client.get_events(baby_uid, 1)

    await session.close()
```

## Note

This project has been set up using PyScaffold 4.5. For details and usage
information on PyScaffold see https://pyscaffold.org/.

```

```
