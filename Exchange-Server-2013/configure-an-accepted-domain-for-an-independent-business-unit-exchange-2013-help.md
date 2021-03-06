﻿---
title: 'Настройка обслуживаемого домена для независимого подразделения'
TOCTitle: Настройка обслуживаемого домена для независимого подразделения
ms:assetid: bc95dbdc-3669-4c06-ab94-90093bc0dbfd
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ657491(v=EXCHG.150)
ms:contentKeyID: 50488959
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка обслуживаемого домена для независимого подразделения

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2014-02-17_

Иногда необходимо настроить обслуживаемый домен для независимой бизнес-единицы с серверами электронной почты вне вашей организации Exchange. В таком случае можно настроить обслуживаемый домен как внешний домен ретрансляции.

## Что нужно знать перед началом работы?

  - Осталось времени до завершения: 5 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Обслуживаемые домены» в разделе [Разрешения потока обработки почты](mail-flow-permissions-exchange-2013-help.md).

  - Если в сети периметра существует подписанный пограничный транспортный сервер, можно настроить обслуживаемые домены на сервере почтовых ящиков в своей организации Exchange. Конфигурация обслуживаемых доменов реплицируется на пограничный транспортный сервер в процессе синхронизации EdgeSync. Дополнительную информацию см. в статье [Пограничные подписки](edge-subscriptions-exchange-2013-help.md).

  - Невозможно создать обслуживаемый домен, имеющий то же имя, что и уже настроенный удаленный домен. Например, если домен fabrikam.com настроен в качестве удаленного домена, нельзя создать обслуживаемый домен fabrikam.com.

  - Перед настройкой обслуживаемого домена необходимо убедиться, что существует общая запись MX в DNS для этого пространства имен SMTP и что эта запись MX ссылается на имя сервера и IP-адрес, связанные с вашей организацией Exchange.

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

> [!TIP]  
> Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.


## Настройка обслуживаемого домена как внешнего домена ретрансляции с помощью Центра администрирования Exchange (EAC)

Может понадобиться настроить обслуживаемый домен для бизнес-единицы с серверами электронной почты вне вашей организации Exchange.

1.  В Центре администрирования Exchange (EAC) выберите **Поток почты** \> **Обслуживаемые домены**, выберите домен, который необходимо настроить, и нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

2.  В поле **Имя** введите отображаемое имя обслуживаемого домена. Каждый обслуживаемый домен вашей организации должны иметь уникальное отображаемое имя. Оно может отличаться от самого обслуживаемого домена. Например, домен Contoso.com может иметь отображаемое имя "Локальный обслуживаемый домен Contoso".

3.  Выберите **Внешний домен ретрансляции**. Это параметр для электронной почты, ретранслируемой на сервер вне вашей организации Exchange.

4.  Нажмите кнопку **Сохранить**.

## Как проверить, что все получилось?

Чтобы убедиться, что обслуживаемый домен успешно настроен как внешний домен ретрансляции, отправьте с него сообщение и проверьте, что оно получено.

