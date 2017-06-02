---
title: "CLR ユーザー定義型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# CLR ユーザー定義型
Microsoft SQL Server では、Microsoft .NET Framework 共通言語ランタイム \(CLR\) を使用して実装されるユーザー定義型 \(UDT\) をサポートしています。  CLR は SQL Server に統合されており、この機構を利用すると、データベースの型システムを拡張できます。  UDT を利用すれば、SQL Server データ型システムのユーザー拡張が可能であり、複雑な構造化型を定義することもできます。  
  
 UDT は、アプリケーション アーキテクチャの観点から見て 2 つの重要な利点を備えています。  
  
-   内部状態と外部動作の間の \(クライアントとサーバーの両方での\) 強力なカプセル化。  
  
-   他の関連するサーバー機能との緊密な統合。  独自の UDT を定義すると、列定義、変数、パラメーター、関数の結果、カーソル、トリガー、およびレプリケーションなど、SQL Server のシステム型を利用できるすべてのコンテキストでその UDT を使用できます。  
  
 詳細については、ご使用中の SQL Server のバージョンに対応するバージョンの SQL Server オンライン ブックを参照してください。  
  
 **SQL Server オンライン ブック**  
  
1.  [ユーザー定義の CLR 型](http://go.microsoft.com/fwlink/?LinkId=98366)  
  
## 参照  
 [Creating SQL Server 2005 Objects In Managed Code](http://msdn.microsoft.com/ja-jp/5358a825-e19b-49aa-8214-674ce5fed1da)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)