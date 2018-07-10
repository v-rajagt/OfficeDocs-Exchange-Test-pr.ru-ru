﻿---
title: 'Отключение или удаление почтового ящика: Exchange 2013 Help'
TOCTitle: Отключение или удаление почтового ящика
ms:assetid: 31ad25d6-2942-4fd9-aecb-cdf9654163d2
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ863434(v=EXCHG.150)
ms:contentKeyID: 50556355
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Отключение или удаление почтового ящика

 

_**Применимо к:**Exchange Server 2013 SP1_

_**Последнее изменение раздела:**2015-03-09_

Вы можете использовать Центр администрирования Exchange или командную консоль для отключения или удаления почтового ящика в Exchange 2013. После отключения или удаления почтового ящика Exchange сохраняет его в базе данных почтовых ящиков и переключает его в отключенное состояние. Отключенные и удаленные почтовые ящики хранятся в базе данных почтовых ящиков до тех пор, пока не истечет срок хранения удаленных почтовых ящиков, который по умолчанию составляет 30 дней. По истечении срока хранения почтовый ящик окончательно удаляется или *очищается*.

Если вам нужно удалить почтовый ящик в Exchange Online, см. статью [Удаление и восстановление почтовых ящиков пользователей в Exchange Online](https://technet.microsoft.com/ru-ru/library/dn186233\(v=exchg.150\)).

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Отключенные или удаленные почтовые ящики называются <em>отсоединенными</em>.</td>
</tr>
</tbody>
</table>


Основное различие между удалением и отключением почтового ящика состоит в следующем: при отключении почтового ящика атрибуты Exchange удаляются из соответствующей учетной записи Active Directory, но учетная запись пользователя сохраняется. При удалении почтового ящика удаляются атрибуты Exchange и учетная запись пользователя Active Directory. Это различие также определяет возможность повторного подключения к отключенным и удаленным почтовым ящикам или их восстановления.

В таблице ниже показано, какие типы почтовых ящиков Exchange можно отключить и удалить.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Тип почтовых ящиков</th>
<th>Отключить?</th>
<th>Удалить?</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Архивный почтовый ящик</p></td>
<td><p>Да</p></td>
<td><p>Нет *</p></td>
</tr>
<tr class="even">
<td><p>Связанный почтовый ящик</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
</tr>
<tr class="odd">
<td><p>Почтовый ящик ресурса (помещение или оборудование)</p></td>
<td><p>Нет</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>Общий почтовый ящик</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
</tr>
<tr class="odd">
<td><p>Почтовый ящик пользователя</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
</tr>
</tbody>
</table>


\* Если включен архивный почтовый ящик, он будет удален при удалении основного почтового ящика. Дополнительные сведения об отключении архивных почтовых ящиков см. в разделе [Управление архивами на месте в Exchange 2013](manage-in-place-archives-in-exchange-2013-exchange-2013-help.md).

Если администратор удаляет учетную запись пользователя с почтовым ящиком, то банк сообщений Exchange со временем обнаружит, что почтовый ящик больше не подключен к учетной записи пользователя, и отметит этот почтовый ящик для удаления, даже если он находится на удержании. Чтобы сохранить почтовый ящик, выполните следующие действия.

1.  Не удаляйте учетную запись пользователя, а отключите ее.

2.  Измените свойства почтового ящика, чтобы ограничить его использование и доступ к нему. Например, установите для квот на отправку и получение значение 1, заблокируйте потенциальных отправителей сообщений на этот почтовый ящик и ограничьте возможность доступа к нему.

3.  Храните почтовый ящик, пока все данные не будут удалены или пока не исчезнет потребность в удержании.

Дополнительные задачи управления, связанные с отключенными почтовыми ящиками, приведены в следующих разделах.

  - [Отключенные почтовые ящики](disconnected-mailboxes-exchange-2013-help.md)

  - [Подключение отключенного почтового ящика](connect-a-disabled-mailbox-exchange-2013-help.md)

  - [Подключение или восстановление удаленного почтового ящика](connect-or-restore-a-deleted-mailbox-exchange-2013-help.md)

  - [Окончательное удаление почтового ящика](permanently-delete-a-mailbox-exchange-2013-help.md)

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения каждой процедуры: 2 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Тема "Разрешения подготовки получателей" в разделе [Разрешения получателей](recipients-permissions-exchange-2013-help.md).

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


## Что необходимо сделать?

## Отключение почтового ящика

Как указывалось ранее, при отключении почтового ящика атрибуты Exchange удаляются из соответствующей учетной записи пользователя Active Directory, но сама учетная запись пользователя сохраняется.

## Использование центра администрирования Exchange для отключения почтового ящика

В следующей процедуре показано, как отключить почтовый ящик пользователя. Эта же процедура используется для отключения почтовых ящиков других типов после перехода на соответствующую страницу в центре администрирования Exchange.

1.  В центре администрирования Exchange перейдите к разделу **Получатели** \> **Почтовые ящики**.

2.  В списке почтовых ящиков пользователя щелкните почтовый ящик, который необходимо отключить.

3.  Нажмите кнопки **Дополнительно**![Значок дополнительных параметров](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Значок дополнительных параметров") и **Отключить**.

4.  Отобразится предупреждение с запросом на подтверждение отключения почтового ящика. Нажмите кнопку **Да**, чтобы отключить почтовый ящик.

Почтовый ящик удаляется из списка почтовых ящиков.

## Использование командной консоли Exchange для отключения почтового ящика

Следующая команда используется для отключения почтовых ящиков пользователя, связанных почтовых ящиков, почтовых ящиков ресурсов и общих почтовых ящиков.

    Disable-Mailbox <identity>

При выполнении данной команды отобразится сообщение с запросом на подтверждение отключения почтового ящика.

Ниже приведено несколько примеров команд для отключения почтовых ящиков.

    Disable-Mailbox danj

    Disable-Mailbox "Conf Room 31/1234 (12)"

    Disable-Mailbox sharedmbx@contoso.com

## Как проверить, что все получилось?

Чтобы убедиться, что почтовый ящик успешно отключен, выполните одно из следующих действий.

  - В центре администрирования Exchange щелкните **Получатели**, перейдите на соответствующую страницу типа отключенного почтового ящика, а затем убедитесь, что почтовый ящик отсутствует в списке.

  - В средстве "Пользователи и компьютеры Active Directory" щелкните правой кнопкой мыши учетную запись пользователя, почтовый ящик которого отключен, и выберите пункт **Свойства**. Обратите внимание, что поле **Электронная почта** на вкладке **Общие** пустое. Таким образом, почтовый ящик отключен, но учетная запись пользователя все еще существует.

  - В консоли Shell выполните следующую команду:
    
        Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisplayName -eq "<display name>" } | fl DisconnectReason,DisconnectDate
    
    Значение `Disabled` свойства *DisconnectReason* указывает, что почтовый ящик отключен.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>При удалении почтового ящика свойству <em>DisconnectReason</em> также присваивается значение <code>Disabled</code>. Однако удаляется соответствующая учетная запись пользователя Active Directory.</td>
    </tr>
    </tbody>
    </table>


  - В консоли Shell выполните следующую команду:
    
        Get-User <identity>
    
    Обратите внимание, что свойство *RecipientType* имеет значение `User`, а не `UserMailbox`, которое является значением для пользователей с включенными почтовыми ящиками. Также подтверждается, что почтовый ящик отключен, но учетная запись пользователя сохранена.

## Удаление почтового ящика

Как указывалось ранее, при удалении почтового ящика удаляются атрибуты Exchange и учетная запись пользователя Active Directory. Почтовый ящик (и архивный почтовый ящик, если он включен) будет окончательно удален из базы данных почтовых ящиков по истечении срока его хранения.

## Использование центра администрирования Exchange для удаления почтового ящика

В следующей процедуре показано, как удалить почтовый ящик пользователя. Эта же процедура используется для удаления почтовых ящиков других типов после перехода на соответствующую страницу в центре администрирования Exchange.

1.  В центре администрирования Exchange перейдите к разделу **Получатели** \> **Почтовые ящики**.

2.  В списке почтовых ящиков пользователя щелкните почтовый ящик, который необходимо удалить, а затем выберите команду **Удалить**![Значок удаления](images/Dd979797.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Значок удаления").

3.  Отобразится предупреждение с запросом на подтверждение удаления почтового ящика. Нажмите кнопку **Да**, чтобы удалить почтовый ящик.

Почтовый ящик удаляется из списка почтовых ящиков.

## Удаление почтового ящика с помощью центра администрирования Exchange

Следующая команда используется для удаления почтовых ящиков пользователя, связанных почтовых ящиков, почтовых ящиков ресурсов и общих почтовых ящиков.

    Remove-Mailbox <identity>

При выполнении данной команды отобразится сообщение с запросом на подтверждение удаления почтового ящика и соответствующей учетной записи Active Directory.

Ниже приведено несколько примеров команд для удаления почтовых ящиков.

    Remove-Mailbox pilarp@contoso.com

    Remove-Mailbox "Fleet Van (16)"

    Remove-Mailbox corpprint

## Как проверить, что все получилось?

Чтобы убедиться, что почтовый ящик успешно удален, выполните один из следующих наборов процедур по проверке.

1.  В центре администрирования Exchange щелкните **Получатели**, перейдите на соответствующую страницу типа удаленного почтового ящика, а затем убедитесь, что почтовый ящик отсутствует в списке.

2.  В средстве "Пользователи и компьютеры Active Directory" убедитесь, что соответствующей учетной записи пользователя нет в списке.

Или

1.  Выполните следующую команду, чтобы убедиться, что почтовый ящик удален.
    
        Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisplayName -eq "<display name>" } | fl DisconnectReason,DisconnectDate
    
    Значение `Disabled` свойства *DisconnectReason* указывает, что почтовый ящик удален.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>При отключении почтового ящика свойству <em>DisconnectReason</em> также присваивается значение <code>Disabled</code>. Однако сохраняется соответствующая учетная запись пользователя Active Directory.</td>
    </tr>
    </tbody>
    </table>


2.  Выполните следующую команду, чтобы убедиться, что учетная запись пользователя Active Directory удалена.
    
        Get-User <identity>
    
    Команда вернет ошибку (не удалось найти пользователя), что подтверждает удаление учетной записи.
