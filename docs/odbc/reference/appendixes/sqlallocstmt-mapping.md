---
title: SQLAllocStmt 對應 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLAllocStmt
- SQLAllocStmt function [ODBC], mapping
ms.assetid: a2449dbb-1b6c-4b49-81b9-ebdddd4442fd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 330c245d8b5839fd8a721a7399a22edea78a2417
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47819966"
---
# <a name="sqlallocstmt-mapping"></a>SQLAllocStmt 對應
當應用程式呼叫**SQLAllocStmt**透過 ODBC 3 *.x*驅動程式，會呼叫：  
  
```  
SQLAllocStmt(hdbc, phstmt)  
```  
  
 對應至**SQLAllocHandle**透過驅動程式管理員在驅動程式中，如下所示：  
  
```  
SQLAllocHandle(SQL_HANDLE_STMT, InputHandle, OutputHandlePtr)  
```  
  
 具有*InputHandle*設為*hdbc*並*OutputHandlePtr*設定為*phstmt*。
