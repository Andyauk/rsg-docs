# Commands

### Core

<details>

<summary>/tp [id / x] [opt: y] [opt: z]- teleport to player or location</summary>

Teleports you to either a player with the given `id` or to a given `x, y, z` location

**Permission level:** admin

* **id or x** - (required) The player id or x coordinate
* **y** - (optional) The y coordinate (required if using x for the first argument)
* **z** - (optional) The z coordinate (required if using x for the first argument)

</details>

<details>

<summary>/tpm - teleport to a marked location</summary>

Teleports you to the marked location on the map.&#x20;

**Permission level:** admin

</details>

<details>

<summary>/togglepvp - toggle PVP on server</summary>

Toggles Player vs Player mode on the server

**Permission level:** admin

</details>

<details>

<summary>/addpermission [id] [permission] - gives a player a permission</summary>

Gives a player with the given `id` the given `permission` level. The player must be online.

**Permission level:** god

</details>

<details>

<summary>/removepermission [id] [permission] - removes a player permission</summary>

Removes the given `permission` from the player with the given `id`. The player must be online.

**Permission level:** god

</details>

<details>

<summary>/openserver - open the server for everyone</summary>

Opens the server allowing everyone to join.

**Permission level:** admin

</details>

<details>

<summary>/closeserver [reason] - close the server for people without permission</summary>

Closes the server for people without the correct permission. Kicks any players currently online without the required permission giving the `reason` in the kick message.&#x20;

**Permission level:** admin

</details>

<details>

<summary>/car [model] - spawns a vehicle</summary>

Spawns a vehicle of the given `model` type.

**Permission level:** admin

</details>

<details>

<summary>/dv - delete vehicle</summary>

Deletes the vehicle you are sitting in or deletes all vehicles within 5.0 units of your position.

**Permission level:** admin

</details>

<details>

<summary>/givemoney [id] [type] [amount] - give money to a player</summary>

Gives money to a player

**Permission level:** admin

* **id** - (required) The `id` of the player
* **type** - (required) The money type \[cash, bank etc...]
* **amount** - (required) The amount to give

</details>

<details>

<summary>/setmoney [id] [type] [amount] - set the amount of money a player has</summary>

Sets the amount of money a player has.

**Permission level:** admin

* **id** - (required) The `id` of the player
* **type** - (required) The money type \[cash, bank etc...]
* **amount** - (required) The amount to set

</details>

<details>

<summary>/job - display your current job</summary>

Displays your current job name and grade

**Permission level:** user

</details>

<details>

<summary>/setjob [id] [job] [grade] - sets a players job</summary>

Sets a player with the given `id` to have the given `job` with the given `grade`

**Permission level:** admin

* **id -** (required) The `id` of the player
* **job** - (required) The job name
* **grade** - (required) The job grade

</details>

<details>

<summary>/gang - display your current gang</summary>

Displays your current gang name and grade

**Permission level:** user

</details>

<details>

<summary>/setgang [id] [gang] [grade] - sets a players gang</summary>

Sets a player with the given `id` to be part of the given `gang` with the given `grade`

**Permission level:** admin

* **id** - (required) The `id` of the player
* **gang** - (required) The gang name
* **grade** (required) The gang grade

</details>

<details>

<summary>/clearinv [opt: id]- clears a players inventory</summary>

Clears the inventory of a player with the given `id` or your own inventory if no `id` is given

**Permission level:** admin

* **id** - (optional) The id of a player

</details>

<details>

<summary>/ooc [message] - ooc chat command</summary>

Sends an out-of-character (ooc) message to the chat.

**Permission level:** user

* **message** - (required) The message to send

</details>

<details>

<summary>/me [message] - shows a message above your head</summary>

Shows a 3d text message above your head. Useful for enhancing roleplay.

**Permission level:** user

* **message** - (required) The message to display

</details>
