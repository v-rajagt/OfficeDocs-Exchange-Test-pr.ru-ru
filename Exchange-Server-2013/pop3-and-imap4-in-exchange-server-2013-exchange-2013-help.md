﻿---
title: 'POP3 и IMAP4 в Exchange Server 2013: Exchange 2013 Help'
TOCTitle: Протоколы POP3 и IMAP4
ms:assetid: a7dc91ee-2919-4db3-ae9c-cd665d2e09ea
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ657728(v=EXCHG.150)
ms:contentKeyID: 50488791
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# POP3 и IMAP4 в Exchange Server 2013

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2016-08-16_

Узнайте о различиях между протоколами POP3 и IMAP4 в Exchange Server 2013 и о том, как настраивать параметры доступа к почтовым ящикам Exchange 2013 для различных почтовых программ.

По умолчанию в Exchange Server 2013 протоколы POP3 и IMAP4 отключены. Для поддержки POP3-клиентов, которые все еще используют эти протоколы, необходимо запустить две службы POP3: службу Microsoft Exchange POP3 и внутреннюю службу Microsoft Exchange POP3. Для поддержки IMAP4-клиентов, которые все еще используют эти протоколы, необходимо запустить две службы IMAP4: службу Microsoft Exchange IMAP4 и внутреннюю службу Microsoft Exchange IMAP4.

Процедуру включения служб POP3 и IMAP4 см. в разделах [Включение протокола POP3 в Exchange 2013](enable-pop3-in-exchange-2013-exchange-2013-help.md) и [Включение протокола IMAP4 в Exchange 2016](enable-imap4-in-exchange-2013-exchange-2013-help.md).

По умолчанию пользователи почтовых ящиков на компьютерах под управлением Exchange 2013 могут получать доступ к своим почтовым ящикам с помощью Outlook или Outlook Web App, Exchange ActiveSync или голосового доступа к Outlook. Outlook, Outlook Web App и голосовой доступ к Outlook позволяют пользователям электронной почты использовать полный набор возможностей, доступных пользователям с почтовыми ящиками на серверах Exchange 2016.

**Содержание**

Общие сведения о функциональных возможностях протоколов POP3 и IMAP4

Межсайтовое подключение на основе протоколов POP3 и IMAP4

Использование нестандартных учетных записей с протоколами POP3 и IMAP4

Общие сведения о различиях между протоколами POP3 и IMAP4

Параметры отправки и получения для почтовых приложений на основе протоколов POP3 и IMAP4

Приложения на основе POP3 и IMAP4

Настройка доступа к почтовым ящикам Exchange 2013 на основе протокола POP3 или IMAP4

## Общие сведения о функциональных возможностях протоколов POP3 и IMAP4

В этом разделе описываются функциональные возможности POP3 и IMAP4 для Exchange 2013.

Протоколы POP3 и IMAP4 имеют следующие преимущества и ограничения.

  - **POP3**. Протокол POP3 был разработан для поддержки автономной обработки почты. При использовании протокола POP3 сообщения электронной почты удаляются с сервера и хранятся на локальном POP3-клиенте, если на этом клиенте не указано сохранять почту на сервере. Это возлагает задачи управления данными и обеспечения безопасности на пользователя. Протокол POP3 не поддерживает расширенные функции совместной работы, например ведение календаря, контакты и задачи.

  - **IMAP4.**. Протокол IMAP4 предусматривает как автономный доступ, так и доступ по сети, однако, как и в случае с протоколом POP3, IMAP4 не поддерживает расширенные функции совместной работы, например ведение календаря, контакты и задачи.

Почтовые приложения на основе протоколов POP3 и IMAP4 не используют эти протоколы для отправки сообщений на почтовый сервер. Чтобы отправлять сообщения, они используют протокол SMTP. Соединитель для приема электронной почты, отправленной из клиентских приложений, которые используют протокол POP3 или IMAP4, автоматически создается при установке Exchange. Дополнительные сведения о соединителях см. в статье [Соединители получения](receive-connectors-exchange-2013-help.md).

> [!NOTE]  
> Каждый раз, когда пользователи открывают программу электронной почты на основе протокола POP или IMAP, чтобы прочитать почту в Office 365, может возникать задержка в несколько секунд. Эта задержка вызвана прокси-сервером, который вводит дополнительный прыжок для проверки подлинности. Сначала прокси-сервер ищет назначенный сервер клиентского доступа и проверяет подлинность на нем.


## Межсайтовое подключение на основе протоколов POP3 и IMAP4

В более ранних версиях Exchange для подключения клиентов POP3 и IMAP4 к почтовым ящикам, расположенным на другом сайте организации, требовалась настройка вручную. По умолчанию Exchange 2013 автоматически перенаправляет подключение с сервера клиентского доступа, находящего на одном сайте, на требуемый сервер.

## Использование нестандартных учетных записей с протоколами POP3 и IMAP4

Для входа в почтовый ящик Exchange 2016 по протоколам POP3 или IMAP4 невозможно использовать анонимную учетную запись или учетную запись гостя. Анонимные учетные записи блокируются из-за уязвимостей, возникающих при использовании нестандартных учетных записей для доступа по протоколам POP3 и IMAP4. Кроме того, к почтовому ящику администратора невозможно подключиться по протоколу POP3 или IMAP4. Это ограничение реализовано в Exchange 2013 для повышения безопасности почтового ящика администратора. Для доступа к почтовому ящику администратора необходимо использовать Outlook или Outlook Web App.

## Общие сведения о различиях между протоколами POP3 и IMAP4

**POP3** — это популярный почтовый протокол IP. По умолчанию при загрузке почтовыми приложениями на основе протокола POP3 сообщений на клиентский компьютер эти сообщения удаляются с сервера. Если копия электронной почты пользователя не хранится на почтовом сервере, он не может получать доступ к одним и тем же сообщениям с нескольких компьютеров. Тем не менее некоторые почтовые приложения на основе протокола POP3 можно настроить для хранения копий сообщений на сервере, чтобы к ним можно было получить доступ с другого компьютера. Клиентские приложения на основе протокола POP3 загружают сообщения с почтового сервера только в одну папку на клиентском компьютере (обычно это папка "Входящие"). С помощью протокола POP3 невозможно синхронизировать несколько папок на почтовом сервере с несколькими папками на клиентском компьютере.

**IMAP4:**  клиентские почтовые приложения, использующие протокол IMAP4, более гибки. Обычно они предлагают больше возможностей, чем клиентские приложения, поддерживающие протокол POP3. По умолчанию при загрузке почтовыми приложениями на основе протокола IMAP4 сообщений на клиентский компьютер копии этих сообщений сохраняются на почтовом сервере. Так как копия электронной почты пользователя хранится на почтовом сервере, он может получать доступ к одним и тем же сообщениям с нескольких компьютеров. Пользователи электронной почты на основе протокола IMAP4 могут создавать несколько папок электронной почты на почтовом сервере и получать к ним доступ. Пользователи также могут получать доступ к сообщениям на сервере с различных компьютеров. Например, большинство приложений IMAP4 можно настроить для хранения копии отправленных сообщений на сервере, чтобы пользователи могли просматривать их с другого компьютера. Протокол IMAP4 поддерживает дополнительные возможности, которые реализованы в большинстве приложений IMAP4. Например, некоторые приложения на основе IMAP4 предоставляют возможность, позволяющую пользователям просматривать только заголовки сообщений на сервере (имена отправителей и темы), а затем загружать только те сообщения, которые требуется прочитать.

> [!NOTE]  
> Клиенты POP3 и IMAP4 имеют ограниченный доступ к сведениям календаря для Exchange. Дополнительные сведения см. в разделах <a href="configure-calendar-options-for-pop3-exchange-2013-help.md">Настройка параметров календаря для службы POP3</a> и <a href="configure-calendar-options-for-imap4-exchange-2013-help.md">Настройка параметров календаря для IMAP4</a>.


## Параметры отправки и получения для почтовых приложений на основе протоколов POP3 и IMAP4

Почтовые приложения на основе POP3 и IMAP4 позволяют пользователям выбирать, когда требуется подключиться к серверу для отправки и получения электронной почты. В этом разделе рассмотрены некоторые наиболее распространенные параметры подключения, а также факторы, которые необходимо учитывать при выборе параметров подключения в почтовых приложениях на основе POP3 и IMAP4.

## Общие параметры конфигурации

В большинстве клиентских программ с поддержкой протоколов POP3 и IMAP4 можно задать три такие параметра:

  - Отправлять и получать почту при каждом запуске почтового приложения. Если используется этот параметр, почта отправляется и принимается только при запуске почтового приложения пользователем.

  - Принимать и отправлять почту вручную. Если используется этот параметр, почта отправляется и принимается при нажатии кнопки "Отправить и получить" в пользовательском интерфейсе клиента.

  - Отправлять и получать почту через заданный промежуток времени. Когда пользователю включает этот параметр, клиентское приложение подключается к серверу через заданный интервал времени для отправки сообщений и загрузки новых сообщений.

Дополнительные сведения о настройке этих параметров в используемом почтовом приложении см. в справочной документации такого приложения.

## Рекомендации по настройке параметров отправки и получения

Если устройство или компьютер, на котором работает программа электронной почты с поддержкой протоколов POP3 или IMAP4, всегда подключены к Интернету, пользователи могут настроить эту программу для отправки и приема сообщений через заданный интервал (в минутах). Частые подключения к серверу позволяют обеспечивать соответствие данных в программе электронной почты последним сведениям на сервере. Однако если устройство или компьютер, на котором работает программа электронной почты с поддержкой протоколов POP3 или IMAP4, всегда подключены к Интернету, можно настроить эту программу для отправки и приема сообщений вручную.

> [!NOTE]  
> При использовании почтового приложения на основе IMAP4, поддерживающего команду IMAP4 IDLE, можно отправлять и получать электронную почту в почтовом ящике Exchange практически в режиме реального времени. Для использования этого способа подключения почтовое серверное приложение и клиентское приложение должны поддерживать команду IMAP4 IDLE. В большинстве случаев пользователям не требуется настраивать параметры приложения IMAP4 для использования этого способа подключения.


## Приложения на основе POP3 и IMAP4

Поскольку Exchange 2013 поддерживает протоколы POP3 и IMAP4, для подключения к Exchange 2013 можно использовать различные клиентские приложения POP3 и IMAP4. К ним относятся Outlook, Outlook Web App Почта Windows Live, Outlook Express, Entourage и многие приложения сторонних производителей, например Gmail, Mozilla Thunderbird и Eudora. Возможности, поддерживаемые отдельными клиентскими почтовыми приложениями, различаются. Дополнительные сведения о конкретных возможностях, предлагаемых клиентскими приложениями POP3 и IMAP4, см. в документации к этим приложениям.

## Настройка доступа к почтовым ящикам Exchange 2013 на основе протокола POP3 или IMAP4

После разрешения клиентского доступа по протоколам POP3 и IMAP4 необходимо предоставить пользователям сведения, необходимые для подключения почтовых программ к почтовым ящикам Exchange 2016.

Чтобы подключиться в пределах корпоративной сети, пользователям потребуется наличие следующих сведений:

  - внутреннее имя сервера POP3 или IMAP4;

  - внутренний номер порта POP3 или IMAP4;

  - внутренний метод шифрования POP3 или IMAP4;

  - внутреннее имя SMTP (сервера исходящей почты);

  - внутренний номер порта SMTP (сервера исходящей почты);

  - внутренний метод шифрования SMTP (сервера исходящей почты)

Чтобы подключиться из Интернета, пользователям потребуется наличие следующих сведений:

  - внешнее имя сервера POP3 или IMAP4;

  - внешний номер порта POP3 или IMAP4;

  - внешний метод шифрования POP3 или IMAP4;

  - внешнее имя SMTP (сервера исходящей почты);

  - внешний номер порта SMTP (сервера исходящей почты);

  - внешний метод шифрования SMTP (сервера исходящей почты)

Пользователям можно предоставить доступ к этим параметрам с помощью электронной почты или других способов взаимодействия вручную. Кроме того, систему Exchange можно настроить таким образом, чтобы пользователи могли просматривать собственные параметры с помощью приложения Outlook Web App.

**Настройка сервера Exchange таким образом, чтобы пользователи могли просматривать свои параметры POP3-, IMAP4- и SMTP-серверов**

По умолчанию пользователи не могут просматривать параметры POP3-, IMAP4-, и SMTP-серверов через Outlook Web App. Чтобы предоставить пользователям такую возможность, необходимо использовать командлеты **Set-PopSettings** и **Set-ImapSettings**. Чтобы разрешить пользователям просматривать свои параметры SMTP-сервера (исходящая почта), необходимо использовать командлет **Set-ReceiveConnector**.

Чтобы пользователи могли просматривать свои параметры POP3, IMAP4 и SMTP, выполните следующие действия:

  - **Параметры POP3**. Запустите командлет **Set-POPSettings** с параметром *ExternalConnectionSettings*. Используйте формат `Set-POPSettings -ExternalConnectionSetting {<FQDN>:995:SSL}`. Например, выполните команду `Set-PopSettings -ExternalConnectionSetting {Dublin01.Contoso.com:995:SSL}`, чтобы клиенты, подключающиеся через сервер с полным доменным именем Dublin01.Contoso.com, могли просматривать свои параметры POP.
    
    После применения этого параметра необходимо перезапустить службы IIS.

  - **Параметры IMAP4**. Запустите командлет **Set-IMAPSettings** с параметром *ExternalConnectionSettings*. Используйте формат `Set-ImapSettings -ExternalConnectionSetting {<FQDN>:993:SSL}`. Например, выполните команду `Set-IMAPSettings -ExternalConnectionSetting {Dublin01.Contoso.com:993:SSL}`, чтобы клиенты, подключающиеся через сервер с полным доменным именем Dublin01.Contoso.com, могли просматривать свои параметры IMAP.
    
    После применения этого параметра необходимо перезапустить службы IIS.

  - **Параметры SMTP**. Запустите командлет **Set-ReceiveConnector** с параметром *AdvertiseClientSettings*. Используйте формат `Set-ReceiveConnector "Client Frontend <Server Name>" -AdvertiseClientSettings $True -FQDN <FQDN>`. Например, выполните команду `Set-ReceiveConnector "Client Frontend <Server Name>" -AdvertiseClientSettings $True -FQDN Dublin01.Contoso.com`, чтобы клиенты, подключающиеся через сервер с полным доменным именем Dublin01.Contoso.com, могли просматривать свои параметры SMTP.
    
    После применения этого параметра необходимо перезапустить службы IIS.

После изменения параметров по умолчанию путем запуска командлетов **Set-POPSettings**, **Set-IMAPSettings** и **Set-ReceiveConnector** пользователи могут просматривать свои внешние параметры POP-, IMAP- и SMTP-серверов в Outlook Web App, последовательно выбирая **Параметры** \> **Параметры** \> **Учетная запись** \> **Моя учетная запись** \> **Параметры для доступа POP или IMAP**.

**Сохранение копий сообщений на сервере**

По умолчанию в некоторых почтовых программах сообщения удаляются с сервера после доставки. Порекомендуйте пользователям настроить почтовые программы таким образом, чтобы копии всех сообщений, получаемых клиентом, сохранялись на сервере. Хранение копий сообщений на сервере позволяет получать доступ к сообщениям с помощью другой почтовой программы.

