﻿---
title: 'Удаление политики адресов электронной почты: Exchange 2013 Help'
TOCTitle: Удаление политики адресов электронной почты
ms:assetid: f1d05223-7d41-406d-8fae-f4227be1c1c2
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb125181(v=EXCHG.150)
ms:contentKeyID: 50489491
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Удаление политики адресов электронной почты

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2012-10-13_

По умолчанию в Exchange существует политика адресов электронной почты, которая определяет псевдоним получателя как локальную часть адреса электронной почты и использует обслуживаемый домен по умолчанию. Локальная часть адреса электронной почты — это имя перед знаком @. Эта политика адресов электронной почты применяется ко всем пользователям в организации. Политику адресов электронной почты удалить невозможно.

Дополнительные сведения об управленческих задачах, связанных с политиками адресов электронной почты, см. в разделе [Процедуры политики адресов электронной почты](email-address-policy-procedures-exchange-2013-help.md).

## Что нужно для начала?

  - Осталось времени до завершения: 5 минут.

  - В случае удаления политики адресов электронной почты, используемой получателями в качестве основной, если не настроены другие политики для получателей, будет использоваться политика по умолчанию.

  - Политику по умолчанию удалить невозможно. Чтобы удалить политику по умолчанию, необходимо сначала назначить другую политику по умолчанию.

  - Если удаляемая политика адресов электронной почты содержит более 3 000 получателей, для выполнения этой процедуры необходимо использовать командную консоль.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Политики адресов электронной почты" в разделе [Адреса электронной почты и адресные книги](email-addresses-and-address-books-exchange-2013-help.md) topic.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/JJ983803.warning(EXCHG.150).gif" title="Предупреждение" alt="Предупреждение" />Предупреждение.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.</td>
</tr>
</tbody>
</table>


## Что необходимо сделать?

## Использование Центра администрирования Exchange для удаления политики адресов электронной почты

1.  Откройте раздел **Поток почты** \> **Политики адресов электронной почты**.

2.  Выберите из списка политику адресов электронной почты, которую необходимо удалить, и нажмите кнопку **Удалить**![Значок удаления](images/Dd979797.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Значок удаления").

3.  В сообщении предупреждения нажмите **Да**, чтобы удалить политику.

## Использование командной консоли для удаления политики адресов электронной почты

В этом примере выполняется удаление политики адресов электронной почты юго-восточных филиалов.

    Remove-EmailAddressPolicy -Identity "South East Offices"

Введите **Y**, чтобы подтвердить удаление политики, а затем нажмите клавишу ВВОД.

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Remove-EmailAddressPolicy](https://technet.microsoft.com/ru-ru/library/bb124504\(v=exchg.150\)).
