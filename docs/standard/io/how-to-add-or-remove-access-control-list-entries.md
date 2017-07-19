---
title: "方法 : アクセス制御リスト エントリを追加または削除する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アクセス制御エントリ [.NET Framework]"
  - "アクセス制御リスト [.NET Framework]"
  - "ACE [.NET Framework]"
  - "ACL [.NET Framework]"
  - "I/O [.NET Framework], アクセス制御リストのエントリ"
ms.assetid: 53758b39-bd9b-4640-bb04-cad5ed8d0abf
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : アクセス制御リスト エントリを追加または削除する
ファイルでアクセス制御リスト \(ACL\) エントリを追加または削除するには、<xref:System.Security.AccessControl.FileSecurity> または <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトをファイルまたはディレクトリから取得して変更し、元のファイルまたはディレクトリに適用する必要があります。  
  
### ファイルで ACL エントリの追加または削除を行うには  
  
1.  <xref:System.IO.File.GetAccessControl%2A> メソッドを呼び出して、ファイルの現在の ACL エントリを含む <xref:System.Security.AccessControl.FileSecurity> オブジェクトを取得します。  
  
2.  手順 1. から返された <xref:System.Security.AccessControl.FileSecurity> オブジェクトで ACL エントリの追加または削除を行います。  
  
3.  <xref:System.Security.AccessControl.FileSecurity> オブジェクトを <xref:System.IO.File.SetAccessControl%2A> メソッドに渡し、変更を適用します。  
  
### ディレクトリで ACL エントリの追加または削除を行うには  
  
1.  <xref:System.IO.Directory.GetAccessControl%2A> メソッドを呼び出して、ディレクトリの現在の ACL エントリを含む <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトを取得します。  
  
2.  手順 1. から返された <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトで ACL エントリの追加または削除を行います。  
  
3.  <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトを <xref:System.IO.Directory.SetAccessControl%2A> メソッドに渡し、変更を適用します。  
  
## 使用例  
 [!code-cpp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/cpp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/cpp/sample.cpp#1)]
 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
## コードのコンパイル  
 この例を実行するには、有効なユーザーまたはグループ アカウントを指定する必要があります。  この例では <xref:System.IO.File> オブジェクトを使用していますが、<xref:System.IO.FileInfo>、<xref:System.IO.Directory>、および <xref:System.IO.DirectoryInfo> クラスにも同じ手順が使用されます。