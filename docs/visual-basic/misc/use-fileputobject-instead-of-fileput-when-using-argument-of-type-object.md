---
title: "使用して &#39;FilePutObject &#39;代わりに &#39;です。FilePut &#39;型 &#39; オブジェクト &#39; の引数を使用する場合"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cba4af206e2dbf767fdb883ec81229a67842c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a>使用して &#39;FilePutObject &#39;代わりに &#39;です。FilePut &#39;型 &#39; オブジェクト &#39; の引数を使用する場合
`FilePut`メソッドには、型の引数が含まれています。`Object`です。 あいまいさを避けるため、`FilePutObject` の代わりに `FilePut` を使用する必要があります。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   `FilePut` を `FilePutObject`に置き換えます。  
  
-   `Object` 引数をより具体的な種類にキャストします。  
  
-   `My.Computer.FileSystem` オブジェクトで利用できる機能を使用します。  
  
## <a name="see-also"></a>関連項目  
 [ビルド内にありません: FilePutObject 関数](http://msdn.microsoft.com/en-us/a0f52a1c-5ecc-4945-b18c-03147af61d6b)  
 [My.Computer.FileSystem オブジェクト](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)  
 [My.Computer.FileSystem.WriteAllBytes メソッド](http://msdn.microsoft.com/en-us/b1a24dc1-eac8-4e22-8ffa-cc3bacbaf826)
