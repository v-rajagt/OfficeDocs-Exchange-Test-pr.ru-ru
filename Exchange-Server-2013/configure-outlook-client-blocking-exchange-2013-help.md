﻿---
title: 'Настройка блокирования клиентов Outlook: Exchange 2013 Help'
TOCTitle: Настройка блокирования клиентов Outlook
ms:assetid: 3a579c83-8bc7-4adc-a25c-8eb6eed7220c
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd335207(v=EXCHG.150)
ms:contentKeyID: 51408018
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка блокирования клиентов Outlook

 

_**Применимо к:** Exchange Server 2010 Service Pack 2 (SP2), Exchange Server 2013_

_**Последнее изменение раздела:** 2015-03-09_

В Microsoft Exchange Server 2013 можно использовать политики сохранения и управляемые папки для управления записями сообщений (MRM). Доступ ко всем соответствующим клиентским функциям для соблюдения политик хранения имеют только пользователи Microsoft Outlook 2010 и более поздних версий. Однако помощник по работе с управляемыми папками применяет политики сохранения к серверу почтовых ящиков независимо от версии клиента Outlook у пользователя. Старые клиенты Outlook не предоставляют функциональность управления записями сообщений. Например, так как Outlook 2007 не поддерживает политики сохранения, пользователи не могут использовать личные теги для элементов и папок.

Вы можете запретить пользователям старых версий Outlook работать с почтовыми ящиками Exchange. Доступ можно заблокировать для отдельных почтовых ящиков или отдельных серверов клиентского доступа.

Сведения о других задачах управления, связанных с управлением записями сообщений (MRM), см. в статье [Процедуры управления записями сообщений](messaging-records-management-procedures-exchange-2013-help.md).

## Доступность функций управления записями сообщений в различных версиях клиентских приложений

Следующая таблица содержит список функций управления записями сообщений, доступных в различных версиях клиентских приложений.

### Функции управления записями сообщений

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Клиентское приложение</th>
<th>Доступные клиентские функции управления записями сообщений</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Outlook 2013 и Outlook 2010</p></td>
<td><p>Все</p></td>
</tr>
<tr class="even">
<td><p>Outlook 2007</p></td>
<td><p>Управляемые папки</p></td>
</tr>
<tr class="odd">
<td><p>Outlook 2003 и более поздних версий</p></td>
<td><p>Не поддерживается</p></td>
</tr>
<tr class="even">
<td><p>Другие клиенты электронной почты</p></td>
<td><p>Нет</p></td>
</tr>
</tbody>
</table>


В следующей таблице показаны номера версий для Outlook.

### Версии Outlook

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Версия Outlook</th>
<th>Номер версии</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Outlook 2013</p></td>
<td><p>15</p></td>
</tr>
<tr class="even">
<td><p>Outlook 2010</p></td>
<td><p>14</p></td>
</tr>
<tr class="odd">
<td><p>Outlook 2007</p></td>
<td><p>12</p></td>
</tr>
<tr class="even">
<td><p>Outlook 2003</p></td>
<td><p>11</p></td>
</tr>
<tr class="odd">
<td><p>Outlook 2002</p></td>
<td><p>10</p></td>
</tr>
<tr class="even">
<td><p>Outlook 2000</p></td>
<td><p>9</p></td>
</tr>
<tr class="odd">
<td><p>Outlook 98</p></td>
<td><p>8.5</p></td>
</tr>
<tr class="even">
<td><p>Outlook 97</p></td>
<td><p>8</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Перед внесением изменений обратите внимание на то, что на строку версии клиента могут влиять установленные исправления и пакеты обновления. Будьте осторожны при ограничении клиентского доступа, так как серверные компоненты Exchange также используют MAPI для входа. Некоторые компоненты указывают свою версию клиента в виде имени компонента (например, SMTP или OLE DB), а другие указывают номер сборки Exchange (например, 6.0.4712.0). Поэтому не рекомендуется ограничивать клиенты, номера версий которых начинаются с 6.&lt;<em>x</em>.<em>x</em>.&gt;. Например, чтобы полностью запретить доступ MAPI, укажите два диапазона вместо <strong>0.0.0-6.5535.65535.65535</strong>, чтобы обеспечить вход в систему серверных компонентов. Например, укажите следующее: <strong>0.0.0-5.9.9; 7.0.0-</strong>.


После выполнения этих процедур необходимо учитывать, что при блокировании доступа пользователей к почтовым ящикам будет отображаться следующее предупреждающее сообщение:


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>«Используемая версия Outlook заблокирована администратором сервера Exchange. Обратитесь к администратору».</p></td>
</tr>
</tbody>
</table>


Чтобы обойти отображение предупреждения о том, что функции управления записями сообщений не поддерживаются для клиентов электронной почты с более ранними версиями Outlook, чем Outlook 2010, можно использовать параметр *ManagedFolderMailboxPolicyAllowed* командлетов **New-Mailbox**, **Enable-Mailbox** и **Set-Mailbox** в командной консоли Exchange. Если политика почтовых ящиков управляемых папок назначена почтовому ящику с помощью параметра *ManagedFolderMailboxPolicy*, то по умолчанию отображается предупреждение, если только не используется параметр *ManagedFolderMailboxPolicyAllowed*.

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 1 минута.

  - Для выполнения этих процедур нельзя использовать Центр администрирования Exchange. Необходимо использовать командную консоль.

  - Для процедур в этом разделе требуются особые разрешения. См. информацию о разрешениях по каждой процедуре.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) или [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

## Что необходимо сделать?

## Версии блока Outlook для каждого почтового ящика

Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Почтовые ящики пользователей» в разделе [Разрешения получателей](recipients-permissions-exchange-2013-help.md).

В этом примере блокируются все версии Outlook до 11.8010.8036.

    Set-CASMailbox -Identity adam@contoso.com -MAPIBlockOutlookVersions "-11.8010.8036"

В этом примере показано, как восстановить доступ к почтовому ящику, заблокированному в версии Outlook.

    Set-CASMailbox -Identity adam@contoso.com -MAPIBlockOutlookVersions $null

Дополнительные сведения о синтаксисе и параметрах см. в статье [Set-CASMailbox](https://technet.microsoft.com/ru-ru/library/bb125264\(v=exchg.150\)).

## Версии блока Outlook на сервере клиентского доступа

Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Подраздел «Параметры службы клиентского доступа RPC» в разделе [Разрешения клиентов и мобильных устройств](clients-and-mobile-devices-permissions-exchange-2013-help.md).

В этом примере показывается блокировка клиентов Outlook до версии 12.0.0 — они не смогут получить доступ к почтовым ящикам на сервере клиентского доступа Exchange 2010 или более поздней версии.

> [!IMPORTANT]  
> Значения, используемые с параметром <em>BlockedClientVersions</em>, приводятся в качестве примеров. Определить правильные версии клиентского программного обеспечения можно с помощью анализа файлов журнала клиентского доступа RPC, находящихся в папке <code>%ExchangeInstallPath%Logging\RPC Client Access</code>.


    Set-RpcClientAccess -Server CAS01 -BlockedClientVersions "0.0.0-5.65535.65535;7.0.0;8.02.4-11.65535.65535"

Дополнительные сведения о синтаксисе и параметрах см. в статье [Set-RpcClientAccess](https://technet.microsoft.com/ru-ru/library/dd351072\(v=exchg.150\)).

