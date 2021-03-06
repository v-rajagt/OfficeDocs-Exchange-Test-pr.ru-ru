﻿---
title: 'Виртуализация Exchange 2013: Exchange 2013 Help'
TOCTitle: Виртуализация Exchange 2013
ms:assetid: 36184b2f-4cd9-48f8-b100-867fe4c6b579
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ619301(v=EXCHG.150)
ms:contentKeyID: 50487813
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Виртуализация Exchange 2013

 

_**Применимо к:** Exchange Server 2013_

_**Последнее изменение раздела:** 2017-08-08_

Можно развернуть Microsoft Exchange Server 2013 в виртуализированной среде. В данном разделе дается обзор сценариев, которые поддерживаются для развертывания Exchange 2013 на программное обеспечение для виртуализации оборудования.

**Содержание**

Требования к аппаратной виртуализации

Требования к хранилищу хост-компьютера

Требования к хранилищу Exchange

Требования и рекомендации относительно памяти Exchange

Отказоустойчивый кластер на базе узлов и миграция для Exchange

Следующие термины используются в этом разделе рассмотрена Exchange виртуализации:

  - **"Холодная" загрузка**. *"Холодная" загрузка* — это действие перевода системы из выключенного состояния в состояние "чистой" загрузки операционной системы. Ни одно государство не операционной системы в этом случае сохраняется.

  - **Сохраненное состояние**. При выключении виртуальной машины, как правило, низкоуровневые оболочки способны сохранять состояние виртуальной машины, поэтому при включении питания компьютера он возвращается в это *сохраненное состояние*, а не запускает "холодную" загрузку.

  - **Планируемая миграция**. Когда системный администратор инициирует перемещение виртуальных машин с одного узла низкоуровневой оболочки на другой, действие называется *планируемой миграцией*. Действие может быть один миграции, или системный администратор может настроить автоматизации для перемещения виртуальной машины на временной основе. Плановой миграции также может быть результатом некоторые другие события, происходящие в системе, другие чем сбое в работе аппаратного или программного обеспечения. Exchange Пункт ключ исправен и виртуальная машина должны быть перемещены, по какой-либо причине. Этот перевод может быть сделано через технологии, такие как Live миграции или vMotion. Однако если виртуальная машина Exchange или узел низкоуровневой оболочки, на котором размещена виртуальная машина, находятся в состоянии сбоя, результаты не характеризуются как плановая миграция.

## Требования к аппаратной виртуализации

Корпорация Microsoft поддерживает сервер Exchange 2013 при его работе на основе программного обеспечения виртуализации оборудования только при выполнении всех указанных ниже условий.

  - Запущено программное обеспечение виртуализации оборудования:
    
      - Все версии Windows Server с технологией Hyper-V или Microsoft Hyper-V Server
    
      - Любой сторонний гипервизор, прошедший проверку согласно [программе проверки технологий виртуализации для Windows Server](https://go.microsoft.com/fwlink/p/?linkid=125375).
    
    > [!NOTE]  
    > Развертывание Exchange 2013 у поставщиков инфраструктуры как служба (IaaS) поддерживается, если соблюдаются все требования к поддержке. Если поставщики предоставляют виртуальные машины, к этим относится полная поддержка низкоуровневой оболочки, используемой для виртуальных машин Exchange, и соответствие инфраструктуры, используемой Exchange, требованиям к производительности, которые были установлены во время определения размера. Развертывание на виртуальных машинах Microsoft Azure поддерживается, если все тома хранилища, используемые для баз данных Exchange и журналов транзакций баз данных (включая базы данных транспорта), настроены для расширенного хранилища Azure.


  - Гостевая виртуальная машина Exchange имеет следующие условия:
    
      - на ней запущено приложение Exchange 2013;
    
      - она развертывается на сервере Windows Server 2008 R2 с пакетом обновления 1 (SP1) (или более поздней версии), Windows Server 2012 или Windows Server 2012 R2.

Для развертываний Exchange 2013:

  - В среде виртуализации поддерживаются все роли сервера Exchange 2013.

  - Серверные виртуальные машины Exchange (включая виртуальные машины почтовых ящиков Exchange, которые входят в группу обеспечения доступности баз данных) можно сочетать с централизованной отказоустойчивой кластеризацией и технологией миграции, поскольку виртуальные машины настроены таким образом, что они не сохраняют и не восстанавливают состояние на диске, если переместить или перевести его в автономный режим. Все действия на уровне низкоуровневой оболочки, направленные на обеспечение отказоустойчивости, должны приводить к холодной загрузке при активации виртуальной машины на целевом узле. Любая плановая миграция должна приводить к завершению работы и холодной загрузке или интерактивной миграции с помощью технологий наподобие динамической миграции Hyper-V. Миграция виртуальных машин с использованием низкоуровневой оболочки реализуется поставщиком низкоуровневой оболочки, поэтому следует убедиться, что поставщик проверяет и поддерживает миграцию виртуальных машин Exchange. Корпорация Майкрософт поддерживает динамическую миграцию этих виртуальных машин в Hyper-V.

  - На физическом хост-компьютере можно развертывать только программы для управления (например, антивирусные программы, программы для резервного копирования или программы для управления виртуальными машинами). Никакие другие серверные приложения (например, Exchange, SQL Server, Active Directory или SAP) не следует устанавливать на хост-компьютере. Необходимо выделить хост-компьютер для запуска гостевых виртуальных машин.

  - Некоторые низкоуровневые оболочки поддерживают функции получения снимков виртуальных машин. В снимке виртуальной машины сохраняется рабочее состояние виртуальной машины. Эта функция позволяет сделать несколько снимков виртуальной машины, а затем возвращаться к любому из предыдущих ее состояний, применяя к ней снимок. Однако снимки виртуальных машин могут быть несовместимы с некоторыми приложениями, поэтому их использование может приводить к неожиданным последствиям в случае серверных приложений, поддерживающих данные о состоянии, таких как Exchange. Как следствие, создание снимков ведомой виртуальной машины Exchange не поддерживается.

  - Многие продукты для виртуализации оборудования позволяют указывать количество виртуальных процессоров, которое должно быть выделено каждой из гостевых виртуальных машин. Виртуальные процессоры, расположенные в гостевой виртуальной машине, используют фиксированное число физических ядер в физической системе. Exchange поддерживает отношение числа виртуальных процессоров к числу физических ядер, не превышающее 2:1, хотя рекомендуется отношение 1:1. Например, двухпроцессорная система с четырехъядерными процессорами содержит 8 физических ядер в обслуживающей системе. В системе с такой конфигурацией не следует выделять на все гостевые виртуальные машины более 16 виртуальных процессоров.

  - При вычислении общего количества виртуальных процессоров, необходимых для хост-компьютера, также необходимо учитывать требования к операциям ввода-вывода и операционной системе. В большинстве случаев эквивалентное количество виртуальных процессоров, требуемое в несущей операционной системе для системы, в которой находятся виртуальные машины Exchange, равно 2. При расчете общего отношения числа физических ядер к числу виртуальных процессоров это значение следует использовать в качестве базового числа виртуальных процессоров несущей операционной системы. Если при наблюдении за производительностью несущей операционной системы обнаруживается потребление ресурсов процессоров, превышающее ресурсы двух процессоров, следует соответствующим образом сократить количество виртуальных процессоров, назначенное гостевым машинам, и проверить, что общее соотношение виртуальных процессоров к физическим ядрам не превышает 2:1.

  - Операционная система для ведомого компьютера Exchange должна использовать диск объемом не менее 15 ГБ плюс объем виртуальной памяти, выделенный ведомому компьютеру. Выполнение этого условия необходимо для учета требований к месту, предъявляемых операционной системой и файлом подкачки. Например, если ведомой машине выделено 16 ГБ памяти, минимальное дисковое пространство, необходимое для ведомой операционной системы, составляет 31 ГБ.
    
    Кроме того, можно отключить прямую связь гостевых виртуальных машин с адаптерами шины (HBA) Fibre Channel или SCSI, установленными на хост-компьютере. В таком случае необходимо настроить адаптеры в операционной системе хост-компьютера и предоставить логические номера устройств (LUN) гостевым виртуальным машинам в виде виртуального или транзитного диска.

  - Поддерживается только один способ отправки сообщений на внешние домены из вычислительных ресурсов Azure — ретрансляция через промежуточный узел SMTP. Вычислительный ресурс Azure отправляет сообщение ретранслятору SMTP, а затем поставщик ретрансляции SMTP доставляет сообщение на внешний домен. Microsoft Exchange Online Protection — один из поставщиков ретрансляции SMTP, но существует и ряд сторонних поставщиков. Дополнительные сведения см. в записи блога от команды поддержки Microsoft Azure [Отправка электронных сообщений на внешние домены из вычислительного ресурса Azure](https://go.microsoft.com/fwlink/p/?linkid=799723).

К началу

## Требования к хранилищу хост-компьютера

Для каждого хост-компьютера применяются следующие требования к минимальному месту на диске:

  - Хост-компьютерам в некоторых приложениях виртуализации оборудования может требоваться место для операционной системы и ее компонентов. Например, при запуске Windows Server 2008 R2 с Hyper-V потребуется не менее 10 ГБ, необходимых для Windows Server 2008. Дополнительные сведения см. в статье [Системные требования Windows Server 2008 R2](https://go.microsoft.com/fwlink/p/?linkid=125378). Кроме того, нужно дополнительное место для файла подкачки операционной системы, файлов дампа (файлов восстановления после сбоя) и программного обеспечения управления.

  - Некоторые низкоуровневые оболочки хранят на хост-компьютере файлы, уникальные для каждой гостевой виртуальной машины. Например, в среде Hyper-V для каждой ведомой машины создается и хранится временный файл памяти (с расширением BIN). Размер каждого BIN-файла равен объему памяти, выделенному ведомой машине. Кроме того, для каждой из ведомых машин на хост-компьютере могут создаваться и храниться другие файлы.

  - Если на хост-компьютере используется Windows Server 2012 Hyper-V или Hyper-V 2012 и вы настраиваете отказоустойчивый кластер на физическом компьютере, на котором серверы почтовых ящиков Exchange будут размещены в группе доступности базы данных, рекомендуем следовать советам, приведенным в статье 2872325 базы знаний Майкрософт [Узлы гостевых кластеров в Hyper-V могут быть неспособны к созданию или присоединению](https://support.microsoft.com/kb/2872325).

К началу

## Требования к хранилищу Exchange

Требования для ресурсов хранения, подключенных к виртуализированной Exchange сервера существуют следующие:

  - Каждой из гостевых машин Exchange должно быть выделено достаточное место в хранилище на хост-компьютере под фиксированный диск с операционной системой гостевой машины, временными файлами памяти и соответствующими файлами виртуальной машины, которые находятся на ведущей машине. Кроме того, для каждой ведомой машины Exchange также необходимо выделить достаточное место для очередей сообщений, а также достаточное место для баз данных и файлов журналов на серверах почтовых ящиков.

  - Хранилище, используемое ведомым компьютером сервера Exchange для хранения данных Exchange (например, баз данных почтовых ящиков или транспортных очередей), может быть виртуальным хранилищем фиксированного размера (например, фиксированные виртуальные жесткие диски (VHD или VHDX) в среде Hyper-V), динамическим виртуальных хранилищем, использующим VHDX-файлы с Hyper-V, транзитным хранилищем SCSI или интернет-хранилищем SCSI (iSCSI). Транзитное хранилище — это хранилище, настроенное на уровне узла и выделенное для одной ведомой машины. Все хранилища, используемые ведомым компьютером с Exchange для хранения данных Exchange, должны быть хранилищами уровня блоков, поскольку система Exchange 2013 не поддерживает тома запоминающих устройств, подключенных к сети (NAS), кроме тех, что указаны в сценарии SMB 3.0 ниже в этом разделе. Кроме того, не поддерживается запоминающее устройство NAS, представленное для ведомого компьютера через низкоуровневую оболочку как хранилище уровня блоков.

  - Фиксированные или динамические виртуальные диски можно хранить в файлах SMB 3.0 на основе хранилища на уровне блока, если ведомый компьютер работает под управлением Windows Server 2012 Hyper-V (или более поздней версии Hyper-V). Файловые ресурсы SMB 3.0 поддерживаются только для хранения фиксированных или динамических дисков. Такие файловые ресурсы не могут использоваться для непосредственного хранения данных Exchange. При использовании файловых ресурсов SMB 3.0 для хранения фиксированных или динамических виртуальных дисков хранилище для поддержки файлового ресурса необходимо настроить для обеспечения высокой доступности, чтобы гарантировать максимальную доступность службы Exchange.

  - Хранилище, используемое сервером Exchange, должно находиться на дисках, отличных от тех, на которых размещается операционная система ведомой виртуальной машины.

  - Хранилище iSCSI можно настроить на использование инициатора iSCSI в ведомой виртуальной машине Exchange. Однако производительность в этой конфигурации будет менее высокой, если сетевой стек виртуальной машины ограничен по функциональности (например, не все виртуальные сетевые стеки поддерживают кадры крупного размера).

К началу

## Требования и рекомендации относительно памяти Exchange

Некоторые низкоуровневые оболочки могут перезаписывать или динамически регулировать объем памяти, доступный для определенной гостевой машины, с учетом использования ею памяти, а также потребностей других гостевых машин, которыми управляют. Такая технология эффективна для рабочих нагрузок, при которых какому-либо процессу требуется больший объем памяти на короткий период времени, который затем может быть распределен для других процессов. Однако это не подходит для рабочих нагрузок, предназначенных для использования памяти на постоянной основе. Приложение Exchange, как и многие серверные приложения с оптимизацией производительности, включающие кэширование данных в памяти, восприимчиво к низкой производительности системы и неприемлемым клиентским возможностям, если оно не полностью контролирует память, выделенную для физической или виртуальной машины, на которой выполняется данное приложение. В результате использование возможностей динамической памяти для Exchange не поддерживается.

К началу

## Отказоустойчивый кластер на базе узлов и миграция для Exchange

Ниже приведены ответы на некоторые часто задаваемые вопросы о централизованной отказоустойчивой кластеризации и технологии миграции в группах обеспечения доступности баз данных Exchange 2013.

  - **Корпорация Майкрософт поддерживает технологию третьих сторон миграции?**
    
    Корпорация Майкрософт не может заявить о поддержке интеграции сторонних низкоуровневых оболочек, использующих эти технологии с Exchange, поскольку данные технологии не входят в программу проверки виртуализации серверов (SVVP). Программа проверки виртуализации серверов (SVVP) охватывает другие аспекты поддержки сторонних низкоуровневых оболочек корпорацией Майкрософт. Необходимо убедиться, что поставщика низкоуровневой оболочки поддерживает сочетание их миграции и кластеризации технологии с Exchange. Если поставщик низкоуровневой оболочки поддерживает свою технологию миграции с Exchange, корпорация Майкрософт поддерживает Exchange с этой технологией миграции.

  - **Каким образом Майкрософт определить индивидуальный отказоустойчивый кластер?**
    
    Централизованной отказоустойчивой кластеризации называется любая технология, обеспечивающая автоматическое способности реагировать на отказы узла уровня соответствующие виртуальные машины и запустить на альтернативные серверы. Поддерживается использование этой технологии, поскольку, в сценарий сбоя, скоро виртуальной машины с узла на альтернативном начальной холодной загрузки. Эта технология помогает гарантировать, что виртуальная машина не запускается из сохраненного состояния, которое сохраняется на диске, поскольку она будет устаревшей относительно остальных участников группы обеспечения доступности баз данных.

  - **Что такое поддержка миграции Microsoft?**
    
    Технология миграции называется любая технология, которая позволяет перемещении виртуальной машины с одного главного компьютера на другой компьютер. Этот шаг также может являться автоматизированным перемещением, которое выполняется при балансировке нагрузки на ресурсы, но он не связан со сбоями в системе. Миграции поддерживаются, если виртуальные машины не запускаются из сохраненного состояния, которое сохраняется на диске. Это означает, что технология, которая перемещает виртуальной машины путем передачи государству и памяти виртуальной машины через сеть без простоя поддерживается Exchange. Поставщик сторонней низкоуровневой оболочки должен обеспечить поддержку технологии миграции, а корпорация Майкрософт поддержит использование Exchange в этой конфигурации.

К началу

