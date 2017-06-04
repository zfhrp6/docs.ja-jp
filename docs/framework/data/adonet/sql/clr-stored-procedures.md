---
title: "CLR ストアド プロシージャ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# CLR ストアド プロシージャ
ストアド プロシージャは、スカラー式では使用できないルーチンです。  ストアド プロシージャは、表形式の結果とメッセージをクライアントに返したり、データ定義言語 \(DDL\) ステートメントおよびデータ操作言語 \(DML\) ステートメントを呼び出したり、出力パラメーターを返したりすることができます。  
  
> [!NOTE]
>  Microsoft Visual Basic では、出力パラメーターのサポートが Microsoft Visual C\# と異なります。  パラメーターを参照によって渡す方式を指定し、次に示すように、\<Out\(\)\> 属性を適用して出力パラメーターを指定する必要があります。  
  
```  
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```  
  
 詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。  
  
 **SQL Server オンライン ブック**  
  
1.  [CLR ストアド プロシージャ](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## 参照  
 [Creating SQL Server 2005 Objects In Managed Code](http://msdn.microsoft.com/ja-jp/5358a825-e19b-49aa-8214-674ce5fed1da)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)