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
ms.openlocfilehash: 5612c2bd4dc08f767643d2cd865a2ba1a8210c15
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a>使用して &#39;FilePutObject &#39;代わりに &#39;です。FilePut &#39;型 &#39; オブジェクト &#39; の引数を使用する場合
`FilePut`メソッドには、型の引数が含まれています。`Object`です。 あいまいさを避けるため、`FilePutObject` の代わりに `FilePut` を使用する必要があります。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   `FilePut` を `FilePutObject`に置き換えます。  
  
-   `Object` 引数をより具体的な種類にキャストします。  
  
-   `My.Computer.FileSystem` オブジェクトで利用できる機能を使用します。  
  
## <a name="see-also"></a>参照  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [My.Computer.FileSystem.WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
