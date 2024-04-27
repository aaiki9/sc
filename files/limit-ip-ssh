#!/bin/bash
function send_log(){
CHATID=$(grep -E "^#bot# " "/etc/bot/.bot.db" | cut -d ' ' -f 3)
KEY=$(grep -E "^#bot# " "/etc/bot/.bot.db" | cut -d ' ' -f 2)
TIME="10"
URL="https://api.telegram.org/bot$KEY/sendMessage"
TEXT="
<code>────────────────────</code>
<b>⚠️ NOTIFICATIONS MULTI LOGIN SSH ⚠️</b>
<code>────────────────────</code>
<code>Username  : </code><code>$user</code>
<code>Limit Ip    : </code><code>$iplimit</code>
<code>────────────────────</code>
"
curl -s --max-time $TIME -d "chat_id=$CHATID&disable_web_page_preview=1&text=$TEXT&parse_mode=html" $URL >/dev/null
}
mulog=$(member)
date=$(date)
data=( `ls /etc/kyt/limit/ssh/ip`);
for user in "${data[@]}"
do
iplimit=$(cat /etc/kyt/limit/ssh/ip/$user)
cekcek=$(echo -e "$mulog" | grep $user | wc -l);
if [[ $cekcek -gt $iplimit ]]; then
userdel -f -r $user
nais=3
echo -e "$waktu\nRemoved User: $user Login: $cekcek IP Max: $ip IP \n" >> /etc/kyt/log/ssh/ssh.log
else
echo > /dev/null
fi
sleep 30
done
if [[ $nais -gt 1 ]]; then
send_log
telegram-send --pre "$(log-ssh)" > /dev/null & 
else
echo > /dev/null
fi
