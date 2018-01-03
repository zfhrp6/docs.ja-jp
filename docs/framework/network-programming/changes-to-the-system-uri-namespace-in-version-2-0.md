---
title: "バージョン 2.0 での System.Uri 名前空間の変更"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 3ebf74fbe7f2e207af8bf861efece58026148e2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a><span data-ttu-id="064fc-102">バージョン 2.0 での System.Uri 名前空間の変更</span><span class="sxs-lookup"><span data-stu-id="064fc-102">Changes to the System.Uri namespace in Version 2.0</span></span>
<span data-ttu-id="064fc-103"><xref:System.Uri?displayProperty=nameWithType> クラスには、いくつかの変更が加えられました。</span><span class="sxs-lookup"><span data-stu-id="064fc-103">Several changes were made to the <xref:System.Uri?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="064fc-104">これらの変更は、不適切な動作を修正し、利便性とセキュリティを強化するものです。</span><span class="sxs-lookup"><span data-stu-id="064fc-104">These changes fixed incorrect behavior, enhanced usability, and enhanced security.</span></span>  
  
## <a name="obsolete-and-deprecated-members"></a><span data-ttu-id="064fc-105">廃止および非推奨になったメンバー</span><span class="sxs-lookup"><span data-stu-id="064fc-105">Obsolete and Deprecated Members</span></span>  
 <span data-ttu-id="064fc-106">コンストラクター:</span><span class="sxs-lookup"><span data-stu-id="064fc-106">Constructors:</span></span>  
  
-   <span data-ttu-id="064fc-107">`dontEscape` パラメーターを持つすべてのコンストラクター。</span><span class="sxs-lookup"><span data-stu-id="064fc-107">All constructors that have a `dontEscape` parameter.</span></span>  
  
 <span data-ttu-id="064fc-108">メソッド:</span><span class="sxs-lookup"><span data-stu-id="064fc-108">Methods:</span></span>  
  
-   <xref:System.Uri.CheckSecurity%2A>  
  
-   <xref:System.Uri.Escape%2A>  
  
-   <xref:System.Uri.Canonicalize%2A>  
  
-   <xref:System.Uri.Parse%2A>  
  
-   <xref:System.Uri.IsReservedCharacter%2A>  
  
-   <xref:System.Uri.IsBadFileSystemCharacter%2A>  
  
-   <xref:System.Uri.IsExcludedCharacter%2A>  
  
-   <xref:System.Uri.EscapeString%2A>  
  
## <a name="changes"></a><span data-ttu-id="064fc-109">変更</span><span class="sxs-lookup"><span data-stu-id="064fc-109">Changes</span></span>  
  
-   <span data-ttu-id="064fc-110">クエリ部分 (ファイル、FTP など) がないとわかっている URI スキーマの場合、'?' 文字は常にエスケープされ、<xref:System.Uri.Query%2A> 部分の先頭とは見なされません。</span><span class="sxs-lookup"><span data-stu-id="064fc-110">For URI schemes that are known to not have a query part (file, ftp, and others), the '?' character is always escaped and is not considered the beginning of a <xref:System.Uri.Query%2A> part.</span></span>  
  
-   <span data-ttu-id="064fc-111">暗黙的なファイル URI の場合 ("c:\directory\file@name.txt" の形式)、完全なエスケープ解除が要求されている場合、または <xref:System.Uri.LocalPath%2A> が `true` の場合を除き、フラグメント文字 ('#') は常にエスケープされます。</span><span class="sxs-lookup"><span data-stu-id="064fc-111">For implicit file URIs (of the form "c:\directory\file@name.txt"), the fragment character ('#') is always escaped unless full unescaping is requested or <xref:System.Uri.LocalPath%2A> is `true`.</span></span>  
  
-   <span data-ttu-id="064fc-112">UNC ホスト名のサポートは削除されました。国際対応のホスト名を表す IDN 仕様が採用されました。</span><span class="sxs-lookup"><span data-stu-id="064fc-112">UNC hostname support was removed; the IDN specification for representing international hostnames was adopted.</span></span>  
  
-   <span data-ttu-id="064fc-113"><xref:System.Uri.LocalPath%2A> は、常に完全にエスケープされていない文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="064fc-113"><xref:System.Uri.LocalPath%2A> always returns a completely unescaped string.</span></span>  
  
-   <span data-ttu-id="064fc-114"><xref:System.Uri.ToString%2A> は、エスケープされた '%'、'?'、または '#' 文字のエスケープを解除しません。</span><span class="sxs-lookup"><span data-stu-id="064fc-114"><xref:System.Uri.ToString%2A> does not unescape an escaped '%', '?', or '#' character.</span></span>  
  
-   <span data-ttu-id="064fc-115"><xref:System.Uri.Equals%2A> には、等価性チェックの <xref:System.Uri.Query%2A> 部分が含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="064fc-115"><xref:System.Uri.Equals%2A> now includes the <xref:System.Uri.Query%2A> part in the equality check.</span></span>  
  
-   <span data-ttu-id="064fc-116">演算子 "==" と "!=" はオーバーライドされ、<xref:System.Uri.Equals%2A> メソッドにリンクされます。</span><span class="sxs-lookup"><span data-stu-id="064fc-116">Operators "==" and "!=" are overridden and linked to the <xref:System.Uri.Equals%2A> method.</span></span>  
  
-   <span data-ttu-id="064fc-117"><xref:System.Uri.IsLoopback%2A> から、一貫性のある結果が生成されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="064fc-117"><xref:System.Uri.IsLoopback%2A> now produces consistent results.</span></span>  
  
-   <span data-ttu-id="064fc-118">URI "`file:///path`" は、"file://path" に変換されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="064fc-118">The URI "`file:///path`" is no longer translated into "file://path".</span></span>  
  
-   <span data-ttu-id="064fc-119">"#" は、ホスト名終端文字として認識されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="064fc-119">"#" is now recognized as a host name terminator.</span></span> <span data-ttu-id="064fc-120">つまり、"http://consoto.com#fragment" は "http://contoso.com/#fragment" に変換されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="064fc-120">That is, "http://consoto.com#fragment" is now converted to "http://contoso.com/#fragment".</span></span>  
  
-   <span data-ttu-id="064fc-121">基本 URI とフラグメントを結合するときのバグが修正されました。</span><span class="sxs-lookup"><span data-stu-id="064fc-121">A bug when combining a base URI with a fragment has been fixed.</span></span>  
  
-   <span data-ttu-id="064fc-122"><xref:System.Uri.HostNameType%2A> のバグが修正されました。</span><span class="sxs-lookup"><span data-stu-id="064fc-122">A bug in <xref:System.Uri.HostNameType%2A> is fixed.</span></span>  
  
-   <span data-ttu-id="064fc-123">NNTP 解析のバグが修正されました。</span><span class="sxs-lookup"><span data-stu-id="064fc-123">A bug in NNTP parsing is fixed.</span></span>  
  
-   <span data-ttu-id="064fc-124">HTTP:contoso.com という形式 URI では、解説例外をスローされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="064fc-124">A URI of the form HTTP:contoso.com now throws a parsing exception.</span></span>  
  
-   <span data-ttu-id="064fc-125">.NET Framework は、URI のユーザー情報を正しく処理します。</span><span class="sxs-lookup"><span data-stu-id="064fc-125">The Framework correctly handles userinfo in a URI.</span></span>  
  
-   <span data-ttu-id="064fc-126">URI パスの圧縮は、破損した URI がルートを越えてファイル システムを通過しないように修正されました。</span><span class="sxs-lookup"><span data-stu-id="064fc-126">URI path compression is fixed so that a broken URI cannot traverse the file system above the root.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="064fc-127">参照</span><span class="sxs-lookup"><span data-stu-id="064fc-127">See Also</span></span>  
 <xref:System.Uri?displayProperty=nameWithType>
