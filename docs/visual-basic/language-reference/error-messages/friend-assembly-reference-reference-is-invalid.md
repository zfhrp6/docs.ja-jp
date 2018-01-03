---
title: "フレンド アセンブリ参照&lt;参照&gt;が正しくありません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords: BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab1c7c5cc7a7f4ad899df7722769238e05d96e6b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a>フレンド アセンブリ参照&lt;参照&gt;が正しくありません
フレンド アセンブリ参照\<参照 > が無効です。 厳密な名前の署名つきアセンブリはその InternalsVisibleTo 宣言内で公開キーを指定しなければなりません。  
  
 渡すアセンブリ名、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>厳密な名前のアセンブリを識別する属性のコンス トラクターが含まれません、`PublicKey`属性。  
  
 **エラー ID:** BC31535  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  厳密な名前のフレンド アセンブリの公開キーを確認します。 渡される、アセンブリ名の一部として、公開キーを含む、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性コンス トラクターを使用して、`PublicKey`属性。  
  
## <a name="see-also"></a>参照  
 <xref:System.Reflection.AssemblyName>  
 [フレンド アセンブリ](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 

