**** Warning ****

*** for language choice you you have to switch manually to French for the moment by default it is English in the introSolfège diagram box *** to be fixed automatically 

introduction

solfege ear training for child and adults, reconize music notes from nao as a teacher, three levels beginner, intermediate, advanced please read the file readme attached before starting

This app is a small solfege ear training for child and adults people, to reconize music notes by ear, very useful for music ear training,it works in french and english,
it is an alpha version i hope to have a lot of contributions and criticism to help me for fixing bugs and advise
 
i use the new dialog topics. So all the sentences and keywords can be viewved easely and changed in the dialogs topic enu & frf
with these you can change all the dialogs to your own language or improve the dialogs

i suggest to read the dialog topic file before starting, it will help you to notice the keyword used for the app

I apologize because i am beginner in nao and also beginner in python, so i will be very happy for help from anybody to make a better app

for the moment, i am 10% of my goal to make a really good solfege ear training, so it will take time to build a real good app (until v2 or more), i plann to do it next year 
with all the feedback and testing in real life to build a good application

there are three levels in this app: 
beginner : reconize music notes on the medium octave without sharp and flat
intermediate: recosize music notes on the medium octave with sharp and flat notes
adcanced: much more difficult, reconize music notes on three octave with sharp and flat

i suggest strongly to use only the beginner level, the others are much more difficult even for myself and i am pianist amateur

have fun !!! and help me to fix alls bugs and so on

ps: i intend to post 3 mn video on you tube to explain how it works soon

F Rouge

starting the app
change set language French or English in Choregraph, by default it is French
Use tactile Head for starting app
Front = short way direct to the levels
Middle= Beginning of the game and introduction
rear = rest or stop


major issues

nao is blocking after dialog sentence very often, i have to restarst app , i don't understand why if somebody can fix the problem i will be very happy
volume control problem i don't succeed to manage automatically if somebody can fix it
recognition problem in english dialog, probably my translation is not correct and prunonciation too, not good in english to be fixed 

it will stay in alpha revision xxx until all the bugs and bad recognition will be fixed then i hope to build the version1 before the end of the year after your remarks and contributions from anybody 
if you want for fix bugs

minor issues

automatic language settings should be implemented, you have to switch manually for the moment in the choregraph 
some bugs which i don't understand for the moment should be fixed
the random function is not working very well or is not well implemented should e fixed


futur improvments for version 2.xx (schedule next year)

i use virtual keyboard for generate piano sound, it is not so good quality sound, i have a real piano so i will improve it but i need to buy midi harware and so on 
with better translation and dialog more interactive i will improve recognition and emotionnal to be much better, but it will take time to do this probably i need some practice with it
the dialog is very poor for the moment need to be more rich with animations
Animation also are very poor also need to make timeline and improvement

next step V3 and more
with solfege training you can do a lot of things, this app is just a starting point for many solfege app with Nao to improve the skills of beginner and amateur musicians


# english topic dialog (extract from *.enu dialog topic below for improving and understanding and keyword for recognition)

concept: (note)
[C D E F G A B
"{the} key {is} C"
"{the} key {is} D"
"{the} key {is} E"
"{the} key {is} F"
"{the} key {is} G"
"{the} key {is} A"
"{the} key {is} B"
"C sharp"
"D sharp"
"E sharp"
"F sharp"
"G sharp"
"D flat"
"E flat"
"G flat"
"A flat"
"B flat"
]

concept: (trick)
[trick soluce
"{too} difficult"
]

# begining of dialog for ear trainning

u:(e:introduction) %intro "Hello, What is your first name ?  tell me  \pau=300\ pass \pau=200\  if i dont reconize your first name " 
    u1:(_~surname) "I understood your first name is   :"  $1 $surname = $1 
    ^goto(debut)
    u1:(~pass) ok  $surname = "Human" 
    ^goto(debut)

u:(~confirm) %debut $surname I will begin a small lesson of solfege, first a short introduction,tell me if you know already the game yes or no ?
    u1:(~confirm) %suite "which level do you choose ? Beginner ,,, intermediate ,,, advanced ? answer me  !"
        u2:(débutant) "ok  " $onSuite ="beginner"
        u2:(intermediaire) "ok you prefer reconize the alterations in sharp or flat, \pau=200\say \pau=200\ sharp, or flat !  " 
            u3:(diezz) "ok go " $onSuite ="interm" $onTon = "sharp"
            u3:(bémol) "ok go " $onSuite = "interm" $onTon = "flat"
        u2:(avancé) "ok you prefer reconize the alterations in sharp or flat, \pau=200\say \pau=200\ sharp, or flat !  " 
            u3:(diezz) "ok go " $onSuite ="advanced" $onTon = "sharp"
            u3:(bémol) "ok go " $onSuite = "advanced" $onTon = "flat"
    u1:(~negative) this will allow to reconize the music keys,\pau=300\ I will play for you music keys from C to B,\pau=400\ tu will try to reconize what i played and pronounce me the key to guess, \pau=300\ If i have difficulties to reconize the key say for example \pau=300\ Key \pau=300\ C \pau=300\ instead of \pau=300\ C alone,  \pau= 400\ you have to choose between three levels,\pau=350\ first the beginner level on medium octave without alteration sharp or flat,\pau=400\ the the intermediate level with sharp and flat, \pau=300\ at leat advanced level on three octave with sharp and flat, \pau=400\ at any moment you can stop the game with stop keyword or rest and now we go next \pau=400\ ^goto(suite)
        
    u1:(~repeat) ^goto(debut)
    u1:(~cancel) "ok I rest "  $onSuite = "ko"
    
        
u:(e:directJeu) "beginner, intermediate, advanced"
    u1:(débutant) "ok  " $onSuite ="beginner"
    u1:(intermediaire) "ok you prefer reconize the alterations in sharp or flat, \pau=200\say \pau=200\ sharp, or flat !  " 
        u2:(diezz) "ok go " $onSuite ="interm" $onTon = "sharp"
        u2:(bémol) "ok go " $onSuite ="interm" $onTon = "flat"
    u1:(avancé) "ok you prefer reconize the alterations in sharp or flat, \pau=200\say \pau=200\ sharp, or flat !  " 
        u2:(diezz) "ok go " $onSuite ="interm" $onTon = "sharp"
        u2:(bémol) "ok go " $onSuite ="interm" $onTon = "flat"
    u1:(~cancel) "ok I rest " $onSuite = "ko"
    

       
        
u:(e:answerHuman) %retouranswer do you have an idea ?
    u1:(_~note) $notefound = $1 $onAns = "found"
    u1:(~repeat)%repete ok $onAns = "repeat" 
    u1:(~pass) ok next key $onAns = "passe" 
    u1:(~help) i can repeat or play you a scale to help you !,you can also say  \pau=250\ next for guessing a new key or introduction to restart the game \pau=200\ say \pau=200\ repeat, scale, next  or \pau=250\ trick for alteration help ! \pau=300\ if i dont reconize a key, you can also say \pau=300\ Key \pau=300\ C for example, \pau=250\ instead of C alone \pau=300\ ^gotoReactivate(retouranswer)
    u1:(~negative)  " The key to guess is \pau=200\ :  $Guess   \pau=200\ and now i play you another key " $onAnswer = "next"
    u1:(~cancel) "ok I rest myself now" $onAns = "end"
    u1:(~trick) do you want to know if the key to guess contain alteration say yes or no ?
        u2:(~confirm) the pitch is  \pau=250\ $Accidental ^gotoReactivate(retouranswerfalse)
        u2:(~negative) ^gotoReactivate(retouranswerfalse)
    u1:(_~begin) "ok I restart the game \pau=200\ " ^gotoReactivate(intro)
    u1:(scale one) " ok go " $Scale = "gammesimpleoctave1" $onAns = "scale"
    u1:(scale two) " ok go" $Scale = "gammesimpleoctave2" $onAns = "scale"
    u1:(scale three) " ok go" $Scale = "gammesimpleoctave3" $onAns = "scale"
    u1:(~gamme) %gamme "scale ! ok go , simple or complete ?  " 
        u2:(simple) ok which octave do you choose ? one, two or three? 
            u3:(one) "ok " $Scale = "gammesimpleoctave1" $onAns = "scale"
            u3:(two) "ok " $Scale = "gammesimpleoctave2" $onAns = "scale"
            u3:(three) "ok " $Scale = "gammesimpleoctave3" $onAns = "scale"
        u2:(complete) "ok " $Scale = "gammecomplete" $onAns = "scale"
        