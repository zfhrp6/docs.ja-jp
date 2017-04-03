---
title: "-target:winmdobj (C# コンパイラ オプション) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7581ec18db0d2741452b47ad6200482b63c102be
ms.lasthandoff: 03/13/2017

---
# <a name="targetwinmdobj-c-compiler-options"></a>/target:winmdobj (C# コンパイラ オプション)
**/target:winmdobj** コンパイラ オプションを使用すると、コンパイラは、Windows ランタイム バイナリ (.winmd) ファイルに変換できる .winmdobj 中間ファイルを作成します。 .winmd ファイルは、マネージ言語プログラムだけでなく JavaScript および C++ プログラムでも使用できます。  
  
## <a name="syntax"></a>構文  
  
```  
/target:winmdobj  
```  
  
## <a name="remarks"></a>コメント  
 **winmdobj** 設定は、中間モジュールが必要であることをコンパイラに通知します。 これに対し、Visual Studio が C# クラス ライブラリを .winmdobj ファイルとしてコンパイルします。 その後、.winmdobj ファイルは <xref:Microsoft.Build.Tasks.WinMDExp> エクスポート ツールで送信され、Windows メタデータ (.winmd) ファイルが生成されます。 .winmd ファイルには、元のライブラリのコードと WinMD メタデータの両方が含まれています。メタデータは、JavaScript または C++、および Windows ランタイムで使用されます。  
  
 **/target:winmdobj** コンパイラ オプションを使用してコンパイルされたファイルの出力は、WimMDExp エクスポート ツール用の入力としてのみ使用するように設計されています。.winmdobj ファイル自体は直接参照されません。  
  
 [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) オプションを使用しない限り、出力ファイル名は最初の入力ファイルと同じになります。 [Main](../../../csharp/programming-guide/main-and-command-args/index.md) メソッドは必要ありません。  
  
 コマンド プロンプトで /target:winmdobj オプションを指定すると、次の **/out** または [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) オプションまでのすべてのファイルが、Windows プログラムを作成するために使用されます。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Windows ストア アプリ用に Visual Studio IDE でこのコンパイラ オプションを設定するには  
  
1.  **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、**[プロパティ]** を選択します。  
  
2.  **[アプリケーション]** タブを選択します。  
  
3.  **[出力の種類]** リストで、**[WinMD ファイル]** を選択します。  
  
     **[WinMD ファイル]** オプションは、[!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)] アプリケーション テンプレートでのみ使用できます。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。  
  
## <a name="example"></a>例  
 次のコマンドは .winmdobj 中間ファイルに `filename.cs` をコンパイルします。  
  
```  
csc /target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>関連項目  
 [/target (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
