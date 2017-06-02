---
title: "-addmodule (C# コンパイラ オプション) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /addmodule
dev_langs:
- CSharp
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
caps.latest.revision: 13
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 614dbefbb472ef2cd03fcb1ba7a44f08c450bf4a
ms.contentlocale: ja-jp
ms.lasthandoff: 05/10/2017

---
# <a name="addmodule-c-compiler-options"></a>/addmodule (C# コンパイラ オプション)
このオプションを使用すると、スイッチで作成されたモジュールが現在のコンパイルに追加されます。  
  
## <a name="syntax"></a>構文  
  
```console  
/addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>引数  
 `file`, `file2`  
 メタデータを含む出力ファイル。 このファイルには、アセンブリ マニフェストを含めることができません。 複数のファイルをインポートするには、コンマかセミコロンでファイル名を区切ります。  
  
## <a name="remarks"></a>コメント  
 **/addmodule** で追加したモジュールはすべて、実行時に出力ファイルと同じディレクトリに置かれている必要があります。 つまり、コンパイル時にはあるゆるディレクトリのモジュールを指定できますが、そのモジュールは実行時にアプリケーション ディレクトリに置かれている必要があります。 実行時にモジュールがアプリケーション ディレクトリにない場合、<xref:System.TypeLoadException> が生成されます。  
  
 `file` には、アセンブリを含めることができません。 たとえば、出力ファイルが [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) で作成された場合、そのメタデータは **/addmodule** でインポートできます。  
  
 出力ファイルが **/target:module** ではなく **/target** オプションで作成された場合、そのメタデータは **/addmodule** ではインポートできませんが、[/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) でインポートできます。  
  
 このコンパイラ オプションは Visual Studio では利用できません。プロジェクトはモジュールを参照できません。 また、このコンパイラ オプションをプログラムで変更することはできません。  
  
## <a name="example"></a>例  
 ソース ファイル `input.cs` をコンパイルし、`metad1.netmodule` と `metad2.netmodule` からメタデータを追加し、`out.exe` を生成します。  
  
```console  
csc /addmodule:metad1.netmodule;metad2.netmodule /out:out.exe input.cs  
```  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB 方法: プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [マルチファイル アセンブリ](../../../framework/app-domains/multifile-assemblies.md)   
 [方法: マルチファイル アセンブリをビルドする](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
