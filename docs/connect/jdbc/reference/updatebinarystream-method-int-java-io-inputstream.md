---
title: updateBinaryStream 方法 (int, java.io.InputStream) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1db3a975-c108-45d1-8c0d-14a094f391bd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ee42a7b0941fb3d485aae708a709a4f741d9825
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782866"
---
# <a name="updatebinarystream-method-int-javaioinputstream"></a>updateBinaryStream 方法 (int, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  使用二進位資料流值，更新指定的資料行。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void updateBinaryStream(int columnIndex,  
                               java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>參數  
 *columnIndex*  
  
 指出資料行索引的 **int**。  
  
 *x*  
  
 InputStream 物件。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 UpdateBinaryStream 方法 java.sql.ResultSet 介面中所指定這個 updateBinaryStream 方法。  
  
 使用這個方法來**映像**，**文字**，並**ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]資料型別可能會影響效能。  
  
 這個方法會透過 InputStream 物件將位元組傳遞到選取的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 二進位資料行，例如 binary、varbinary、varbinary(max)、image、xml 和 udt。 這個方法不支援更新字元資料行。 若要以 InputStream 更新字元資料行，請使用 [updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md) 方法。  
  
## <a name="see-also"></a>另請參閱  
 [updateBinaryStream 方法 &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
