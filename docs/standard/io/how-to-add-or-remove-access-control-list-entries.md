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
---
# <a name="how-to-add-or-remove-access-control-list-entries"></a><span data-ttu-id="e603f-102">方法 : アクセス制御リスト エントリを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="e603f-102">How to: Add or Remove Access Control List Entries</span></span>
<span data-ttu-id="e603f-103">ファイルでアクセス制御リスト (ACL) エントリを追加または削除するには、<xref:System.Security.AccessControl.FileSecurity> または <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトをファイルまたはディレクトリから取得して変更し、元のファイルまたはディレクトリに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e603f-103">To add or remove Access Control List (ACL) entries to or from a file, the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object must be obtained from the file or directory, modified, and then applied back to the file or directory.</span></span>  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="e603f-104">ファイルで ACL エントリの追加または削除を行うには</span><span class="sxs-lookup"><span data-stu-id="e603f-104">To add or remove an ACL entry from a File</span></span>  
  
1.  <span data-ttu-id="e603f-105"><xref:System.IO.File.GetAccessControl%2A> メソッドを呼び出して、ファイルの現在の ACL エントリを含む <xref:System.Security.AccessControl.FileSecurity> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="e603f-105">Call the <xref:System.IO.File.GetAccessControl%2A> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2.  <span data-ttu-id="e603f-106">手順 1. から返された <xref:System.Security.AccessControl.FileSecurity> オブジェクトで ACL エントリの追加または削除を行います。</span><span class="sxs-lookup"><span data-stu-id="e603f-106">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3.  <span data-ttu-id="e603f-107"><xref:System.Security.AccessControl.FileSecurity> オブジェクトを <xref:System.IO.File.SetAccessControl%2A> メソッドに渡し、変更を適用します。</span><span class="sxs-lookup"><span data-stu-id="e603f-107">Pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A> method to apply the changes.</span></span>  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="e603f-108">ディレクトリで ACL エントリの追加または削除を行うには</span><span class="sxs-lookup"><span data-stu-id="e603f-108">To add or remove an ACL entry from a Directory</span></span>  
  
1.  <span data-ttu-id="e603f-109"><xref:System.IO.Directory.GetAccessControl%2A> メソッドを呼び出して、ディレクトリの現在の ACL エントリを含む <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="e603f-109">Call the <xref:System.IO.Directory.GetAccessControl%2A> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2.  <span data-ttu-id="e603f-110">手順 1. から返された <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトで ACL エントリの追加または削除を行います。</span><span class="sxs-lookup"><span data-stu-id="e603f-110">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3.  <span data-ttu-id="e603f-111"><xref:System.Security.AccessControl.DirectorySecurity> オブジェクトを <xref:System.IO.Directory.SetAccessControl%2A> メソッドに渡し、変更を適用します。</span><span class="sxs-lookup"><span data-stu-id="e603f-111">Pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A> method to apply the changes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e603f-112">例</span><span class="sxs-lookup"><span data-stu-id="e603f-112">Example</span></span>  
 [!code-cpp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/cpp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/cpp/sample.cpp#1)]
 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e603f-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="e603f-113">Compiling the Code</span></span>  
 <span data-ttu-id="e603f-114">この例を実行するには、有効なユーザーまたはグループ アカウントを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e603f-114">You must supply a valid user or group account to run this example.</span></span> <span data-ttu-id="e603f-115">この例では <xref:System.IO.File> オブジェクトを使用していますが、<xref:System.IO.FileInfo>、<xref:System.IO.Directory>、および <xref:System.IO.DirectoryInfo> クラスにも同じ手順が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e603f-115">This example uses a <xref:System.IO.File> object; however, the same procedure is used for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>
