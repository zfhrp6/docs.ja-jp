---
title: '方法 : アクセス制御リスト エントリを追加または削除する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ACEs [.NET Framework]
- ACLs [.NET Framework]
- access control entries [.NET Framework]
- I/O [.NET Framework], access control list entries
- access control lists [.NET Framework]
ms.assetid: 53758b39-bd9b-4640-bb04-cad5ed8d0abf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 24c428a80f18b35d0aa3119a3c5fa1a6dcb2130e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573424"
---
# <a name="how-to-add-or-remove-access-control-list-entries"></a>方法 : アクセス制御リスト エントリを追加または削除する
ファイルでアクセス制御リスト (ACL) エントリを追加または削除するには、<xref:System.Security.AccessControl.FileSecurity> または <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトをファイルまたはディレクトリから取得して変更し、元のファイルまたはディレクトリに適用する必要があります。  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-file"></a>ファイルで ACL エントリの追加または削除を行うには  
  
1.  <xref:System.IO.File.GetAccessControl%2A> メソッドを呼び出して、ファイルの現在の ACL エントリを含む <xref:System.Security.AccessControl.FileSecurity> オブジェクトを取得します。  
  
2.  手順 1. から返された <xref:System.Security.AccessControl.FileSecurity> オブジェクトで ACL エントリの追加または削除を行います。  
  
3.  <xref:System.Security.AccessControl.FileSecurity> オブジェクトを <xref:System.IO.File.SetAccessControl%2A> メソッドに渡し、変更を適用します。  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-directory"></a>ディレクトリで ACL エントリの追加または削除を行うには  
  
1.  <xref:System.IO.Directory.GetAccessControl%2A> メソッドを呼び出して、ディレクトリの現在の ACL エントリを含む <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトを取得します。  
  
2.  手順 1. から返された <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトで ACL エントリの追加または削除を行います。  
  
3.  <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトを <xref:System.IO.Directory.SetAccessControl%2A> メソッドに渡し、変更を適用します。  
  
## <a name="example"></a>例  
 [!code-cpp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/cpp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/cpp/sample.cpp#1)]
 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例を実行するには、有効なユーザーまたはグループ アカウントを指定する必要があります。 この例では <xref:System.IO.File> オブジェクトを使用していますが、<xref:System.IO.FileInfo>、<xref:System.IO.Directory>、および <xref:System.IO.DirectoryInfo> クラスにも同じ手順が使用されます。
