---
title: "-out (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 332e369b6fe2de79c9063daa9e6d5c0e83f0bcc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="out-c-compiler-options"></a>/out (C# コンパイラ オプション)
**/out** オプションは、出力ファイルの名前を指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
/out:filename  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 コンパイラによって作成された出力ファイルの名前です。  
  
## <a name="remarks"></a>コメント  
 コマンド ラインでは、コンパイル用に複数の出力ファイルを指定することができます。 コンパイラは、**/out** オプションの後に 1 つまたは複数のソース コード ファイルがあることを想定しています。 そしてすべてのソース コード ファイルがその **/out** オプションで指定された出力ファイルにコンパイルされます。  
  
 作成するファイルの完全な名前と拡張子を指定します。  
  
 出力ファイルの名前を指定しない場合:  
  
-   .exe は **Main** メソッドを含むソース コード ファイルからその名前を取得します。  
  
-   .dll または .netmodule は最初のソース コード ファイルからその名前を取得します。  
  
 1 つの出力ファイルをコンパイルするために使用されるソース コード ファイルは、別の出力ファイルのコンパイルの同じコンパイルでは使用できません。  
  
 コマンド ラインのコンパイルで複数の出力ファイルを生成する場合は、出力ファイルのいずれか 1 つだけがアセンブリになれること、および (**/out** で暗黙的または明示的に) 指定された最初の出力ファイルだけがアセンブリになれることに留意してください。  
  
 コンパイルの一部として生成されるすべてのモジュールが、同じくコンパイルで作成されるアセンブリに関連付けらるファイルになります。 [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) を使用して、アセンブリ マニフェストを表示し、関連付けられているファイルを確認します。  
  
 exe をフレンド アセンブリのターゲットにするには、/out コンパイラ オプションが必要です。 詳細については、「[フレンド アセンブリ](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)」を参照してください。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[アプリケーション]** プロパティ ページをクリックします。  
  
3.  **[アセンブリ名]** プロパティを変更します。  
  
     このコンパイラ オプションをプログラムで設定するには: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> は読み取り専用のプロパティで、プロジェクトの種類 (exe、ライブラリなど) と、アセンブリ名の組み合わせによって決まります。 これらのプロパティの一方または両方を変更するには、出力ファイル名を設定する必要があります。  
  
## <a name="example"></a>例  
 `t.cs` をコンパイルして出力ファイル `t.exe` とビルド `t2.cs` を作成し、モジュール出力ファイル `mymodule.netmodule` を作成します。  
  
```console  
csc t.cs /out:mymodule.netmodule /target:module t2.cs  
```  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)  
 [フレンド アセンブリ](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
