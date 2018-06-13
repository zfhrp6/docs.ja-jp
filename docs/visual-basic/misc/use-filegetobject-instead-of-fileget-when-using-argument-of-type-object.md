---
title: 使用して&#39;FileGetObject&#39;の代わりに&#39;FileGet&#39;型の引数を使用するときに&#39;オブジェクト&#39;
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 2edb80f6df95774e0ea5a7b51e57925845d7ba75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640418"
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a>使用して&#39;FileGetObject&#39;の代わりに&#39;FileGet&#39;型の引数を使用するときに&#39;オブジェクト&#39;
`FileGet` メソッドには、型 `Object`の引数が含まれています。 あいまいさを避けるため、`FileGetObject` の代わりに `FileGet` を使用する必要があります。  
  
 `My.Computer.Filesystem` によって提供される機能は、 `FileGet` または `FileGetObject`よりも使いやすく、パフォーマンスが優れています。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  `FileGet` を `FileGetObject`に置き換えます。  
  
2.  `Object` 引数をより具体的な種類にキャストします。  
  
## <a name="see-also"></a>関連項目  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
