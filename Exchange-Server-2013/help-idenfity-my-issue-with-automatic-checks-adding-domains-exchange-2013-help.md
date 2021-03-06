﻿---
title: 'Добавление доменов: определение проблемы с помощью автоматических проверок'
TOCTitle: Помощь в определении проблемы с помощью автоматических проверок — добавление доменов
ms:assetid: ea90a24b-7c9c-48d5-9475-0eb7777452f3
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn793981(v=EXCHG.150)
ms:contentKeyID: 62633055
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Помощь в определении проблемы с помощью автоматических проверок — добавление доменов

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2016-12-09_

Проверки, описанные на этой странице, помогут вам определить некоторые распространенные проблемы при настройке. Вы можете воспользоваться автоматическими проверками ниже, чтобы подтвердить правильность конфигурации и обновить среду.

Если у вас уже есть учетная запись Office 365, нажмите кнопку **Вход**. Вам не понадобится учетная запись Azure ID. Учетная запись пользователя может потребоваться снова при запуске проверок. В таком случае учетные данные включают имя пользователя в формате имя\_пользователя@имя\_office365.домен и пароль.

## Необходимые условия

Мы проверим, установлены ли Помощник по входу в Azure Active Directory и Модуль Azure Active Directory для Windows PowerShell.

Помощник по входу в Azure Active Directory поставляется как две версии: [32-разрядная версия](https://go.microsoft.com/fwlink/?linkid=286261) и [64-разрядный выпуск](https://go.microsoft.com/fwlink/?linkid=286262).

Модуль Azure Active Directory для Windows PowerShell поставляется как две версии: [32-разрядная версия](https://go.microsoft.com/fwlink/?linkid=286258) и [64-разрядный выпуск](https://go.microsoft.com/fwlink/?linkid=286259).

## Добавление проверок домена


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Приложение</p></td>
<td><p>Проблема</p></td>
<td><p>Проверка</p></td>
</tr>
<tr class="even">
<td><p>Домены</p></td>
<td><p>Мне хотелось бы определить, какие локальные домены у меня есть/не знаю, какими доменами я владею.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834925">Выполнять эту проверку</a></p></td>
</tr>
<tr class="odd">
<td><p>Домены</p></td>
<td><p>Как убедиться, что для моего клиента добавлены и проверены правильные домены?</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834905">Выполнять эту проверку</a></p></td>
</tr>
<tr class="even">
<td><p>Домены</p></td>
<td><p>Как убедиться в правильности всех своих DNS-записей для Office 365?</p></td>
<td><ol>
<li><p><a href="https://portal.microsoftonline.com/">Войдите в Office 365</a></p></li>
<li><p>Выберите элемент <a href="https://portal.microsoftonline.com/tools">Сервис</a></p></li>
<li><p>Выберите пункт <strong>Проверка локального ПК с помощью анализатора соответствия рекомендациям для Office 365</strong></p></li>
</ol></td>
</tr>
</tbody>
</table>

