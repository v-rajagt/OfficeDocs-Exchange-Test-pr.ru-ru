﻿---
title: 'Exchange 2013: отправка ответных сообщений об отсутствии через удаленный домен'
TOCTitle: Настройка отправки ответных сообщений об отсутствии на рабочем месте через удаленный домен
ms:assetid: 0c1e56be-7a29-4294-9762-600f9f788741
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ657713(v=EXCHG.150)
ms:contentKeyID: 50487463
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Настройка отправки ответных сообщений об отсутствии на рабочем месте через удаленный домен

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2015-04-08_

Можно воспользоваться командной консолью Exchange, чтобы настроить способ отправки и получения сообщений электронной почты через удаленные домены. В следующем примере демонстрируется, как использовать командную консоль Exchange для настройки способа отправки сообщения об отсутствии на работе в Exchange.

## Что нужно знать перед началом работы?

  - Осталось времени до завершения: 10 минут

  - Для выполнения этой процедуры можно использовать только командную консоль.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Удаленные домены" в разделе [Разрешения потока обработки почты](mail-flow-permissions-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Использование командной консоли для настройки ответов об отсутствии на работе

Командлет **Set-RemoteDomain** используется для настройки свойств удаленного домена.

В этом примере отключаются сообщения об отсутствии на работе для удаленного домена с именем Contoso.

    Set-RemoteDomain Contoso -AllowedOOFType None

В этом примере разрешается прием только внешних сообщений об отсутствии на работе.

    Set-RemoteDomain Contoso -AllowedOOFType External

