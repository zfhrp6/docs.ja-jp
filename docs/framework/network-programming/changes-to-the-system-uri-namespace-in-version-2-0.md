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
ms.openlocfilehash: 906abbcbd3ec00e76d8c183f61828fb5135d9154
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a>バージョン 2.0 での System.Uri 名前空間の変更
<xref:System.Uri?displayProperty=nameWithType> クラスには、いくつかの変更が加えられました。 これらの変更は、不適切な動作を修正し、利便性とセキュリティを強化するものです。  
  
## <a name="obsolete-and-deprecated-members"></a>廃止および非推奨になったメンバー  
 コンストラクター:  
  
-   `dontEscape` パラメーターを持つすべてのコンストラクター。  
  
 メソッド:  
  
-   <xref:System.Uri.CheckSecurity%2A>  
  
-   <xref:System.Uri.Escape%2A>  
  
-   <xref:System.Uri.Canonicalize%2A>  
  
-   <xref:System.Uri.Parse%2A>  
  
-   <xref:System.Uri.IsReservedCharacter%2A>  
  
-   <xref:System.Uri.IsBadFileSystemCharacter%2A>  
  
-   <xref:System.Uri.IsExcludedCharacter%2A>  
  
-   <xref:System.Uri.EscapeString%2A>  
  
## <a name="changes"></a>変更  
  
-   クエリ部分 (ファイル、FTP など) がないとわかっている URI スキーマの場合、'?' 文字は常にエスケープされ、<xref:System.Uri.Query%2A> 部分の先頭とは見なされません。  
  
-   暗黙的なファイル URI の場合 ("c:\directory\file@name.txt" の形式)、完全なエスケープ解除が要求されている場合、または <xref:System.Uri.LocalPath%2A> が `true` の場合を除き、フラグメント文字 ('#') は常にエスケープされます。  
  
-   UNC ホスト名のサポートは削除されました。国際対応のホスト名を表す IDN 仕様が採用されました。  
  
-   <xref:System.Uri.LocalPath%2A> は、常に完全にエスケープされていない文字列を返します。  
  
-   <xref:System.Uri.ToString%2A> は、エスケープされた '%'、'?'、または '#' 文字のエスケープを解除しません。  
  
-   <xref:System.Uri.Equals%2A> には、等価性チェックの <xref:System.Uri.Query%2A> 部分が含まれるようになりました。  
  
-   演算子 "==" と "!=" はオーバーライドされ、<xref:System.Uri.Equals%2A> メソッドにリンクされます。  
  
-   <xref:System.Uri.IsLoopback%2A> から、一貫性のある結果が生成されるようになりました。  
  
-   URI "`file:///path`" は、"file://path" に変換されなくなりました。  
  
-   "#" は、ホスト名終端文字として認識されるようになりました。 つまり、"http://consoto.com#fragment" は "http://contoso.com/#fragment" に変換されるようになりました。  
  
-   基本 URI とフラグメントを結合するときのバグが修正されました。  
  
-   <xref:System.Uri.HostNameType%2A> のバグが修正されました。  
  
-   NNTP 解析のバグが修正されました。  
  
-   HTTP:contoso.com という形式 URI では、解説例外をスローされるようになりました。  
  
-   .NET Framework は、URI のユーザー情報を正しく処理します。  
  
-   URI パスの圧縮は、破損した URI がルートを越えてファイル システムを通過しないように修正されました。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Uri?displayProperty=nameWithType>
