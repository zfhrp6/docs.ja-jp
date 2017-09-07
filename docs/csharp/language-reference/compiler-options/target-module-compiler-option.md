---
title: "-target:module (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /target:module
dev_langs:
- CSharp
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 23c91fe0e4002ebf4c002eb4e0c7e25020fed356
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="targetmodule-c-compiler-options"></a>/target:module (C# コンパイラ オプション)
このオプションでは、コンパイラはアセンブリ マニフェストを生成しません。  
  
## <a name="syntax"></a>構文  
  
```console  
/target:module  
```  
  
## <a name="remarks"></a>コメント  
 既定では、このオプションを使用してコンパイルすることによって作成された出力ファイルに、.netmodule という拡張子が付きます。  
  
 アセンブリ マニフェストのないファイルは、.NET Framework 共通言語ランタイムで読み込むことができません。 ただし、このようなファイルは、[/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) を使用して、アセンブリのアセンブリ マニフェストに組み込むことができます。  
  
 複数のモジュールが 1 回のコンパイルで作成される場合、あるモジュールの [internal](../../../csharp/language-reference/keywords/internal.md) 型をコンパイル中に別のモジュールで使用することができます。 あるモジュールのコードが別のモジュールの `internal` 型を参照する場合は、**/addmodule** を使用して、両方のモジュールをアセンブリ マニフェストに組み込む必要があります。  
  
 Visual Studio 開発環境では、モジュールの作成はサポートされていません。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」をご覧ください。  
  
## <a name="example"></a>例  
 `in.cs` をコンパイルし、`in.netmodule` を作成するには、次のコードを使用します。  
  
```console  
csc /target:module in.cs  
```  
  
## <a name="see-also"></a>関連項目  
 [/target (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)

