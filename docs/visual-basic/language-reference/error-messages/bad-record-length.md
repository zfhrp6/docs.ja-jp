---
title: レコード長が正しくありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: b4b311e2eb504c485772091ed126b3beb71729cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585971"
---
# <a name="bad-record-length"></a>レコード長が正しくありません。
このエラーでは以下の原因が考えられます。  
  
-   指定されたレコードの変数の長さ、 `FileGet`、 `FileGetObject`、`FilePut`または`FilePutObject`ステートメントは、対応する指定された長さによって異なります。`FileOpen`ステートメントです。  
  
-   内の変数、`FilePut`または`FilePutObject`ステートメントまたは可変長文字列が含まれています。  
  
-   内の変数、`FilePut`または`FilePutObject`かが含まれています、`Variant`型です。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  レコードの変数の型を定義するユーザー定義型の固定長変数のサイズの合計と同じでは、値に記載されていることを確認、`FileOpen`ステートメントの`Len`句。  
  
2.  場合内の変数、`FilePut`または`FilePutObject`可変長文字列は、少なくとも 2 文字で指定されたレコードの長さよりも短いかどうかを確認、ステートメントが可変長文字列が含まれていますか、`Len`の句、 `FileOpen`ステートメント。  
  
3.  場合内の変数、`FilePut`または`FilePutObject`かが含まれています、`Variant`可変長の文字列は、少なくとも 4 バイトで指定されたレコードの長さよりも短いかどうかを確認、`Len`の句、`FileOpen`ステートメントです。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
