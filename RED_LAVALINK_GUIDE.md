# Connecting Red-DiscordBot to Pterodactyl Lavalink

This guide explains how to connect your Red-DiscordBot to the Lavalink node running on your Pterodactyl panel.

## Prerequisites

1.  **Lavalink Server**: You must have created and started a server using the Lavalink Egg on your Pterodactyl panel.
2.  **Red-DiscordBot**: You must have a running instance of Red-DiscordBot.

## Step 1: Gather Lavalink Details

From your Pterodactyl panel, go to your Lavalink server and note the following:

-   **Server Address**: The IP address or domain of the node.
-   **Server Port**: The port assigned to the server (usually displayed next to the address, e.g., `192.168.1.1:25565` -> Port is `25565`).
-   **Password**: The password you set in the "Startup" tab or "Variables" tab (Default: `youshallnotpass`).

## Step 2: Configure Red-DiscordBot

You can configure Red-DiscordBot to use this external Lavalink node using the `[p]llset` commands.

1.  **Stop the internal Lavalink (if running)**:
    ```
    [p]llset unmanaged
    ```
    *(Replace `[p]` with your bot's prefix)*

2.  **Add the external node**:
    ```
    [p]llset add <node_name> <host> <port> <password>
    ```
    -   `<node_name>`: A name for this connection (e.g., `pterodactyl-node`).
    -   `<host>`: The IP address or domain of your Pterodactyl Lavalink server.
    -   `<port>`: The port of your Pterodactyl Lavalink server.
    -   `<password>`: The password for your Lavalink server.

    **Example**:
    ```
    [p]llset add pterodactyl-node 192.168.1.100 25565 youshallnotpass
    ```

3.  **Verify Connection**:
    The bot should attempt to connect. You can check the status with:
    ```
    [p]audioset status
    ```

## Troubleshooting

-   **Connection Refused**: Ensure the Pterodactyl server is running and the port is open/allocated correctly.
-   **Authentication Failed**: Check the password in the Pterodactyl "Variables" tab and ensure it matches what you entered in the `llset` command.
-   **Version Mismatch**: Ensure your Red-DiscordBot is up to date, as it requires a compatible Lavalink version. The Egg installs the latest Lavalink by default.
