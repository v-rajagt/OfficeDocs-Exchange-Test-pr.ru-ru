﻿---
title: 'Задание функций почтовых ящиков для пользователей голосового доступа к Outlook: Exchange 2013 Help'
TOCTitle: Задание функций почтовых ящиков для пользователей голосового доступа к Outlook
ms:assetid: 10960bf0-65cf-4d0b-bae5-d203c53662db
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa996307(v=EXCHG.150)
ms:contentKeyID: 50556336
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Задание функций почтовых ящиков для пользователей голосового доступа к Outlook

 

_**Применимо к:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:**2013-02-22_

Голосовой доступ к Outlook содержит два интерфейса: телефонный и голосовой интерфейс пользователя. Параметры телефонного интерфейса пользователя с включенной поддержкой единой системы обмена сообщениями можно настроить при доступе пользователя к почтовому ящику с помощью данной системы в Exchange 2013. При изменении параметров телефонного интерфейса пользователя с включенной поддержкой единой системы обмена сообщениями для политики почтовых ящиков системы это оказывает влияние на всех пользователей, которые связаны с политикой почтовых ящиков системы. Для политики почтовых ящиков единой системы обмена сообщениями можно изменить следующие параметры телефонного интерфейса пользователя.

  - Доступ к голосовой почте без ПИН-кода

  - Голосовые ответы на другие сообщения

  - Доступ к календарю из телефонного интерфейса пользователя

  - Доступ к каталогу из телефонного интерфейса пользователя

  - Доступ к электронной почте из телефонного интерфейса пользователя

  - Доступ к личным контактам из телефонного интерфейса пользователя

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Для изменения параметров голосового интерфейса пользователя голосового доступа к Outlook вы можете использовать только командную консоль.</td>
</tr>
</tbody>
</table>


Дополнительные сведения об управленческих задачах, связанных с политиками почтовых ящиков единой системы обмена сообщениями, см. в разделе [Процедуры политики почтовых ящиков единой системы обмена СООБЩЕНИЯМИ](um-mailbox-policy-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Политики почтовых ящиков единой системы обмена сообщениями» в разделе [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md).

  - Перед выполнением этой процедуры убедитесь, что абонентская группа единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание абонентской группы единой системы обмена сообщениями](create-a-um-dial-plan-exchange-2013-help.md).

  - Перед выполнением этой процедуры убедитесь, что политика почтовых ящиков единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание политики почтовых ящиков единой системы обмена сообщениями](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..</td>
</tr>
</tbody>
</table>


## Использование командной консоли для изменения параметров телефонного интерфейса пользователя для политики почтовых ящиков единой системы обмена сообщениями

В этом примере устанавливаются параметры, связанные с телефонным интерфейсом пользователя, для политики почтовых ящиков единой системы обмена сообщениями с именем `MyUMMailboxPolicy`.

    Set-UMMailbox -identity MyUMMailboxPolicy -AllowSubscriberAccess $true -AllowTUIAccessToCalendar $false -AllowTUIAccessToDirectory $false -AllowTUIAccessToEmail -$true -AllowTUIAccessToPersonalContacts $true
