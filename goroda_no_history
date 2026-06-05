# Что делает бот
# 1. Проверяет есть ли вообще такой город +
# 2. Проверяет был ли использован этот город ранее +
# 3. Проверяет должен ли быть этот город ( по первой букве) +
# 4. Учитывает на какую букву оканьчивается город +
# 5. Если gorod_bot оканчивается на 'ь' или 'ы', то человек должен назвать город на предыдущую букву +
# 6. Записывает ход игры в отдельный документ (hod.txt) (толко после завершения игры - !stop)+
# 7. Если gorod_user оканчивается на 'ь' или 'ы' , то бот должен назвать город на предыдущую букву +
# 8. Понимает большие и маленькие буквы +
# 9. Понимает пробелы и приспосабливает для дальнейших действий +
# 10. Так как в России один город на ' й ' , то после города Йошкар-ола , городов на ' й ' больше не будет +
# 11. Можно попросить помощь у бота (только 2 раза) +
# 12. Если город оканчиватся на 'ый' , то надо назвать город на букву перед этим +

import random
import time

cities=open('F:\goroda_no_h/new_goroda1.txt','r',encoding='utf-8')
# hod=open('F:/goroda/hod.txt','w',encoding='utf-8')

cities_split=[]

for line in cities:
    cities_split.append(line)

randomm=random.randint(1,len(cities_split))
gorod_bot=cities_split[randomm]
gorod_bot=gorod_bot.replace('\n','')
used_goroda=[]

if gorod_bot[len(gorod_bot)-1]=='ь' or gorod_bot[len(gorod_bot)-1]=='ы':
    for i in range(len(cities_split)):
            randomm=random.randint(1,len(cities_split))
            gorod_bot=cities_split[randomm]
            gorod_bot=gorod_bot.replace('\n','')  
            if gorod_bot[len(gorod_bot)-1]!='ь' and gorod_bot[len(gorod_bot)-1]!='ы':
                break
            else:
                continue
used_goroda.append(gorod_bot)
#Стваит большую букву
gorod_bot=gorod_bot.title()
if '_' in gorod_bot:
    gorod_bot=gorod_bot.replace('_',' ')
# Изначальное количество помощи
helpp=2
# Факт помощи
help_fact=False
if_gorod_user_help=1
print( 'Привет! Это бот для того что бы играть в города. Ниже представленны команды!'+'\n'+'!stop - прекращение работы бота'+'\n'+'!restart - полностью заново начать игру'+'\n'+'!help - использование помощи бота (только '+str(helpp)+' раз(а))'+'\n'+'!what - посмотреть что это за город в гугл '+'\n''Город - '+ gorod_bot)   

while 1==1:
    if_gorod_user_iscl=1
    if_gorod_user_help=1
    gorod_user=input('\n'+'Введи город: ')
    if gorod_user=='!restart':
        restart=input('Игра сейчас начнется заново, в уверены что хотите продолжить? да/нет ')
        while restart!='да' or restart!='нет':
            if restart=='да':
                used_goroda=[]
                helpp=2
                print('Игра началась заново, все слова сброшены!')
                if_gorod_user_iscl=1
                if_gorod_user_help=1
                gorod_user=input('\n'+'Введи город: (Предыдущий - '+gorod_bot+')')
                break
            elif restart=='нет':
                print('Хорошо, играйте дальше!)')
                if_gorod_user_iscl=1
                if_gorod_user_help=1
                gorod_user=input('\n'+'Введи город: (Предыдущий - '+gorod_bot+')' )
                break
            else:
                print('Вы ввели что-то непонятное, введите еще раз')        
    if gorod_user=='!help':
        if helpp>0:
            help_fact=True
            helpp-=1
            if gorod_bot[len(gorod_bot)-1]=='й' and gorod_bot[len(gorod_bot)-2]=='ы':
                if_gorod_user_iscl=3
            elif gorod_bot[len(gorod_bot)-1]=='ь' or gorod_bot[len(gorod_bot)-1]=='ы':
                if_gorod_user_iscl=2
            elif gorod_bot[len(gorod_bot)-1]=='й' and 'йошкар-ола' in used_goroda:
                if_gorod_user_iscl=2
            for i in range(len(cities_split)-1):
                gorod_user_help=cities_split[i]
                gorod_user_help=gorod_user_help.replace('\n','')
                    
                if gorod_user_help[0] == gorod_bot[len(gorod_bot)-if_gorod_user_iscl] and gorod_user_help not in used_goroda:
# Менят '_' на пробел (в списке городов вместо пробелов '_')              
                    if '_' in gorod_user_help:
                        gorod_user_help=gorod_user_help.replace('_',' ')
                    used_goroda.append(gorod_user_help)
                    gorod_user_help=gorod_user_help.title()
                    print('Город - ' + gorod_user_help + '( использовалась помощь бота, осталось помощи - ' +str(helpp) +' )'+'\n')            
                    gorod_bot=gorod_user_help
                    gorod_user=input('\n'+'Введи город: ')
                    break
                else:
                    continue
        else:
            print('Помощей не осталось(')
    if gorod_user=='!what':
        print ('Нажми или скопируй ссыллку: '+'https://www.google.com/search?q='+gorod_bot.replace(' ','+')+'+город')
        gorod_user=input('\n'+'Введи город: ')
    if gorod_user=='!stop':
        print('Жду тебя в следующий раз!')
        break

# Делает gorod_user маленьками буквами (в списке городов все города маленькими буквами)
    gorod_user=gorod_user.lower()
# Меняет пробелы на '_' (в списке городов города с пробелами пишутся с '_')
    gorod_user=gorod_user.replace(' ','_')
# Проверка есть ли такой город или нет
    for i in range(len(cities_split)):   
        gorod_bot_proverka=cities_split[i].replace('\n','')
        if gorod_user==gorod_bot_proverka:
            gorod_bot_proverka=True
            break
        else:
            continue
# Проверка трех букв (bot)
    if gorod_bot[len(gorod_bot)-1]=='й' and gorod_bot[len(gorod_bot)-2]=='ы':
        if_gorod_user_iscl=3
    elif gorod_bot[len(gorod_bot)-1]=='ь' or gorod_bot[len(gorod_bot)-1]=='ы' :
        if_gorod_user_iscl=2
    elif gorod_bot[len(gorod_bot)-1]=='й' and 'йошкар-ола' in used_goroda:
        if_gorod_user_iscl=2
# Проверка gorod_user              
    if gorod_bot_proverka!=True or gorod_user[0]!=gorod_bot[len(gorod_bot)-if_gorod_user_iscl] :
        print('Такого города нет в моём словаре или город не на ту букву, введите новый город (город - '+ gorod_bot + ' )')
    elif gorod_user in used_goroda:
        print('Такой город уже был, введите новый город (город - '+ gorod_bot + ' )')
    elif gorod_bot_proverka==True or gorod_user[0]==gorod_user_help[len(gorod_user_help)-if_gorod_user_help]:
# Проверка трех букв (user)
# Ставится если gorod_user оканчсивается на 'ь' или 'ы' , так же с 'й', если 'Йошкар-ола' уже была
        if_gorod_user_iscl=1
        if gorod_user[len(gorod_user)-1]=='й' and gorod_user[len(gorod_user)-2]=='ы':
            if_gorod_user_iscl=3
        elif gorod_user[len(gorod_user)-1]=='ь' or gorod_user[len(gorod_user)-1]=='ы':
            if_gorod_user_iscl=2
        elif gorod_user[len(gorod_user)-1]=='й' and 'йошкар-ола' in used_goroda:
            if_gorod_user_iscl=2
# Добавляются в список использованных городов
        used_goroda.append(gorod_user)
# Подбор города на последнюю букву gorod_user
        for i in range(len(cities_split)-1):
            randomm=random.randint(1,len(cities_split)-len(used_goroda))
            gorod_bot=cities_split[randomm]
            gorod_bot=gorod_bot.replace('\n','')
            
            if gorod_bot[0] == gorod_user[len(gorod_user)-if_gorod_user_iscl] and gorod_bot not in used_goroda:

# Менят '_' на пробел (в списке городов вместо пробелов '_')              
                if '_' in gorod_bot:
                    gorod_bot=gorod_bot.replace('_',' ')
                
# Добавляются в список использованных городов
                used_goroda.append(gorod_bot)
                used_goroda.append(gorod_user)
# Записывает города в файл hod.txt
                # hod.write('bot: '+gorod_bot+'\n')
                # if help_fact==False:
                #     hod.write('user: '+gorod_user+'\n')
                # elif help_fact==True:
                #     hod.write('user: '+gorod_user+'\n' +' ( помощь бота, осталось кол-во попыток '+str(helpp)+' )')
                gorod_bot=gorod_bot.title()
                print('.')
                time.sleep(0.5)
                print('..')
                time.sleep(0.5)
                print('...')
                time.sleep(0.5)
                
                if gorod_user[len(gorod_user)-1]=='й' and gorod_user[len(gorod_user)-2]=='ы':
                    print('Город - ' + gorod_bot +  " (город оканчивался на 'ый')" +'\n')
                    break
                elif gorod_user[len(gorod_user)-1]=='ь' or gorod_user[len(gorod_user)-1]=='ы':
                    print('Город - ' + gorod_bot +  " (город оканчивался на 'ь' или 'ы')" +'\n')
                    break           
                elif gorod_user[len(gorod_user)-1]=='й' and 'йошкар-ола' in used_goroda:
                    print('Город - ' + gorod_bot +  " (городов на 'й' больше нет)" +'\n')
                    break
                if gorod_bot[len(gorod_bot)-1]=='й' and gorod_bot[len(gorod_bot)-2]=='ы':
                    print('Город - ' + gorod_bot+" (город оканчивается на 'ый', называйте город на " +"' "+gorod_bot[len(gorod_bot)-3]+" '"+' )'+ '\n')
                    break           
                elif gorod_bot[len(gorod_bot)-1]=='ь' or gorod_bot[len(gorod_bot)-1]=='ы':
                    print('Город - ' + gorod_bot+" (город оканчивается на 'ь' или 'ы', называйте город на " +"' "+gorod_bot[len(gorod_bot)-2]+" '"+' )'+ '\n')
                    break
                elif gorod_bot[len(gorod_bot)-1]=='й' and 'йошкар-ола' in used_goroda:
                    print('Город - ' + gorod_bot+" (город оканчивается на 'й'(Йошкар-Ола уже была), называйте город на " +"' "+gorod_bot[len(gorod_bot)-2]+" '"+' )'+ '\n')
                    break
                
                else:
                    print('Город - ' + gorod_bot + '\n')
                    break
            else:
                continue
cities.close()
# hod.close()
            
            

