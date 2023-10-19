# Apple Magic Keyboard in Linux

I was browsing options for Bluetooth keyboards recently and was lucky to hit an Apple Magic Keyboard for as low as 25 Euro. Once I’ve received the packet I was impassioned to start using it. How disappointed I was when I found out that it pairs only as half-Numpad (in my case only 7–8–9–0 keys were active) and disconnects right after Caps Lock pressed. In the end I’ve found the solution which I would like to share here today.

* Step 1. Make sure the keyboard is off. The best way to do that is to power cycle by removing batteries and plugging them back.

* Step 2. Open terminal. Run the following commands:

    ```bash
    sudo bluetoothctl
    [bluetooth]# power on
    [bluetooth]# agent KeyboardOnly
    [bluetooth]# default-agent
    [bluetooth]# pairable on
    ```
* Step 3. Power on your Magic Keyboard. Hold the power button and do not release until step 5.

* Step 4. In bluetoothctl type:

    ```bash
    [bluetooth]# scan on
    ```

* It will start scanning for available Bluetooth devices. What we are looking for would be indicated like this:

    ```bash
    [NEW] Device 78:CA:39:XX:XX:XX Apple Wireless Keyboard
    ```
    
* Step 5. Copy MAC address for the keyboard from the previous step. Add keyboard as trusted device:

    ```bash
    [bluetooth]# trust 78:CA:39:XX:XX:XX
    Once it trusted start pairing:
    ```

    ```bash
    [bluetooth]# pair 78:CA:39:XX:XX:XX
    Attempting to pair with 78:CA:39:XX:XX:XX
    [CHG] Device 78:CA:39:4F:CA:AF Connected: yes
    [agent] PIN code: 299251
    ```

* Step 5. Release the‘ Power on’ button on the keyboard and type PIN code on the keyboard. It won’t indicate anything in the terminal, but that's fine. Commit PIN by hitting ‘Enter’. If pairing is successful output will be similar to that:

    ```bash
    [CHG] Device 78:CA:39:XX:XX:XX ServicesResolved: yes
    [CHG] Device 78:CA:39:XX:XX:XX Paired: yes
    Pairing successful
    ```
* Step 6. Now your keyboard is paired, but most likely it will be acting as a Numpad. To resolve this issue run following in terminal:

    ```bash
    sudo apt update
    sudo apt install numlockx
    numlockx off
    ```

Probably it also makes sense to add 'numlock off' as startup command in 'gnome-session-properties'
Congratulations — now you have fully working Apple Keyboard!

---

Documentation By: **Raymond C. TURNER**

**Last Update:** Thursday 19th October 2023