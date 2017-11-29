---
title: "#<a name=\"externalsource-directive\"></a>ExternalSource ディレクティブ"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "160"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f90b838e50b65b8652cd9cf6f6ee084e9552f025
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
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
