﻿---
title: 'Пограничные транспортные серверы в гибридных развертываниях: Exchange 2013 Help'
TOCTitle: Пограничные транспортные серверы в гибридных развертываниях
ms:assetid: 166b1490-5c56-40df-a17b-e8bb36224fd9
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Hh134662(v=EXCHG.150)
ms:contentKeyID: 50489589
ms.date: 04/26/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Пограничные транспортные серверы в гибридных развертываниях

 

_**Применимо к:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:**2018-04-16_

Роль пограничного транспортного сервера — это дополнительная роль, которая обычно развертывается на компьютере, размещенном в сети периметра организации Exchange. Она предназначена для уменьшения уязвимости организации. Роль пограничного транспортного сервера обрабатывает весь поток почты через Интернет, обеспечивая ретрансляцию SMTP и работу служб промежуточных узлов для внутренних локальных серверов Exchange Server в организации.

## Пограничные транспортные серверы в организациях с гибридным развертыванием Exchange

Для организаций Exchange 2016, в которых необходимо использовать пограничные транспортные серверы, можно развернуть эти серверы с последним выпуском Exchange 2016 и более поздних версий, Exchange 2013 или Exchange 2010. Используйте пограничные транспортные серверы, если не хотите предоставлять доступ непосредственно к внутренним серверам Exchange через Интернет. Когда вы выполните развертывание пограничного транспортного сервера в гибридной среде, Exchange Online через службу Exchange Online Protection будет подключаться к пограничному транспортному серверу для доставки сообщений. Затем пограничный транспортный сервер будет доставлять эти сообщения на локальный сервер почтовых ящиков Exchange, на котором расположен почтовый ящик получателя.

<table>
<thead>
<tr class="header">
<th><img src="images/Dn151301.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Не размещайте между локальными серверами Exchange и Office 365 серверы, службы или устройства, которые обрабатывают или изменяют SMTP-трафик. Безопасность потока обработки почты между локальной организацией Exchange и Office 365 зависит от информации, которая содержится в отправляемых сообщениях. Поддерживаются брандмауэры, пропускающие SMTP-трафик через TCP-порт 25 без изменений. Когда сервер, служба или устройство обрабатывает сообщение, отправленное из организации Exchange в Office 365 или наоборот, эта информация удаляется. В этом случае сообщение больше не считается внутренним, и на него распространяются правила фильтрации нежелательной почты, транспорта и журнала, а также другие политики.</td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/Dn151301.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если есть другие пограничные транспортные серверы Exchange в расположениях, где они не будут обрабатывать гибридный транспорт, им не требуется обновление для поддержки гибридного развертывания. Если же в дальнейшем планируется подключение EOP к дополнительным пограничным транспортным серверам для гибридного транспорта, на этих серверах необходимо установить Exchange 2016 или более поздней версии, Exchange 2010 или Exchange 2013.</td>
</tr>
</tbody>
</table>


## Добавление пограничного транспортного сервера в гибридную среду

Развертывание пограничного транспортного сервера в локальной организации при настройке гибридной среды — это необязательный шаг. При настройке гибридного развертывания мастер гибридной конфигурации позволяет выбрать один или несколько внутренних локальных серверов Exchange, а также один или несколько локальных пограничных транспортных серверов для обработки передачи гибридной почты в организации Exchange Online.

При добавлении пограничного транспортного сервера в гибридное развертывание он взаимодействует со службой EOP от имени внутренних серверов Exchange. Пограничный транспортный сервер действует в качестве ретранслятора между внутренними серверами Exchange и службой EOP для исходящих сообщений из локальной организации в организацию Exchange Online. Пограничный транспортный сервер также действует в качестве ретранслятора между внутренними серверами Exchange для входящих сообщений из организации Exchange Online в локальную организацию. Все функции безопасности подключений, которые ранее выполнялись внутренними серверами Exchange, теперь выполняются пограничным транспортным сервером. Поиск получателей, политики соответствия требованиям и другие виды проверки сообщений продолжают обрабатываться на внутренних серверах Exchange.

В случае добавления пограничного транспортного сервера в гибридное развертывание нет необходимости направлять через него почту, которой обмениваются пользователи внутри организации с получателями в Интернете. Через пограничный транспортный сервер направляются только сообщения, которыми обмениваются локальные организации и организации Exchange Online.

## Поток почты без пограничного транспортного сервера

Приведенный ниже процесс и схема описывают путь, который проходят сообщения между локальной организацией и Exchange Online в случае отсутствия пограничного транспортного сервера.

1.  Исходящие сообщения из локальной организации для получателей в организации Exchange Online передаются из почтового ящика на внутреннем сервере Exchange.

2.  Сервер Exchange отправляет сообщение непосредственно в службу EOP.

3.  EOP доставляет сообщение в организацию Exchange Online.

Сообщения, отправленные из организации Exchange Online получателям в локальной организации, следуют по обратному маршруту.

**Поток почты в гибридном развертывании без пограничного транспортного сервера**

![Гибридный поток почты без пограничного транспортного сервера](images/Hh134662.a95b4d1e-fd4a-4952-b891-22f84c9e71a3(EXCHG.150).png "Гибридный поток почты без пограничного транспортного сервера")

## Поток обработки почты с пограничным транспортным сервером

Следующий процесс показывает путь, который сообщения проходят между локальной организацией и организацией Exchange Online, если развернут пограничный транспортный сервер. Сообщения из локальной организации для получателей в организации Exchange Online отправляются с внутреннего сервера Exchange:

1.  Сообщения из локальной организации для получателей в организации Exchange Online передаются из почтового ящика на внутреннем сервере Exchange.

2.  Сервер Exchange отправляет сообщение на пограничный транспортный сервер с Exchange поддерживаемой версии и выпуска.

3.  Пограничный транспортный сервер отправляет сообщение в службу EOP.

4.  EOP доставляет сообщение в организацию Exchange Online.

Сообщения, отправленные из организации Exchange Online получателям в локальной организации, следуют по обратному маршруту.

**Поток почты в гибридном развертывании при наличии развернутого пограничного транспортного сервера**

![Гибридный поток почты с пограничным транспортным сервером](images/Hh134662.821fe099-56f5-4501-8e1a-e184ba07a653(EXCHG.150).png "Гибридный поток почты с пограничным транспортным сервером")
