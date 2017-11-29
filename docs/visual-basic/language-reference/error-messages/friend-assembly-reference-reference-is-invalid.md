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
ms.openlocfilehash: 39ae94e309ee8d18e6b5317445b7e4b7f6a42af9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a>フレンド アセンブリ参照&lt;参照&gt;が正しくありません
フレンド アセンブリ参照\<参照 > が無効です。 厳密な名前の署名つきアセンブリはその InternalsVisibleTo 宣言内で公開キーを指定しなければなりません。  
  
 渡すアセンブリ名、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>厳密な名前のアセンブリを識別する属性のコンス トラクターが含まれません、`PublicKey`属性。  
  
 **エラー ID:** BC31535  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  厳密な名前のフレンド アセンブリの公開キーを確認します。 渡される、アセンブリ名の一部として、公開キーを含む、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性コンス トラクターを使用して、`PublicKey`属性。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Reflection.AssemblyName>  
 [フレンド アセンブリ](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)  
 [方法: 署名されたフレンド アセンブリを作成する](http://msdn.microsoft.com/library/f5542300-58b4-4e1c-b809-8df11e95e69b)
