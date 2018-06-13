---
title: '#ExternalSource ディレクティブ'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: 146ab41d74b45acc4063e2463baca26c7caa4652
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586592"
---
# <a name="externalsource-directive"></a>#ExternalSource ディレクティブ
特定のソース コード行と、ソースに外部のテキストの間のマッピングを示します。  
  
## <a name="syntax"></a>構文  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>指定項目  
 `StringLiteral`  
 外部ソースへのパス。  
  
 `IntLiteral`  
 外部ソースの最初の行の行番号。  
  
 `LogicalLine`  
 外部ソースでエラーが発生する行。  
  
 `#End ExternalSource`  
 `#ExternalSource` ブロックを終了します。  
  
## <a name="remarks"></a>コメント  
 このディレクティブは、コンパイラと、デバッガーでのみ使用されます。  
  
 ソース ファイルには、外部ソースのディレクティブには、特定のソース ファイル内のコード行と .aspx ファイルなどのソースに外部のテキストの間のマッピングを示しますが含まれます。 指定されたソース コードでは、コンパイル時にエラーが発生する場合は、外部ソースからのものとして識別されます。  
  
 外部ソース ディレクティブでは、コンパイルに影響を与えるありません、入れ子にすることはできません。 内部使用のみアプリケーションが用意されています。  
  
## <a name="see-also"></a>関連項目  
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
