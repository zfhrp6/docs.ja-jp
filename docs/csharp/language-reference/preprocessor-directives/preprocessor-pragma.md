---
title: '#pragma (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: a4829d5062474922d45a2f4f8e1cddf9023b6ad8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278810"
---
# <a name="pragma-c-reference"></a>#pragma (C# リファレンス)
`#pragma` は、ファイル内に指定され、そのファイルのコンパイルについての特別な命令をコンパイラに指示します。 命令はコンパイラによってサポートされている必要があります。 つまり、`#pragma` を使用してカスタムの前処理命令を作成することはできません。 Microsoft C# コンパイラは、次の 2 つの `#pragma` 命令をサポートしています。  
  
 [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [#pragma checksum](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a>構文  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pragma-name`  
 認識されているプラグマの名前。  
  
 `pragma-arguments`  
 プラグマに固有の引数。  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
 [#pragma checksum](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)
