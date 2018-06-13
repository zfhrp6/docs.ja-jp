---
title: フレンド アセンブリ参照&lt;参照&gt;が正しくありません
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: c47fae9c60dc04ee02b1ff015d3dde87b8920c02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587372"
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a>フレンド アセンブリ参照&lt;参照&gt;が正しくありません
フレンド アセンブリ参照\<参照 > が無効です。 厳密な名前の署名つきアセンブリはその InternalsVisibleTo 宣言内で公開キーを指定しなければなりません。  
  
 渡すアセンブリ名、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>厳密な名前のアセンブリを識別する属性のコンス トラクターが含まれません、`PublicKey`属性。  
  
 **エラー ID:** BC31535  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  厳密な名前のフレンド アセンブリの公開キーを確認します。 渡される、アセンブリ名の一部として、公開キーを含む、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性コンス トラクターを使用して、`PublicKey`属性。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Reflection.AssemblyName>  
 [フレンド アセンブリ](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 

