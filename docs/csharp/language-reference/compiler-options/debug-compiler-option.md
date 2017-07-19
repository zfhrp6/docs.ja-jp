---
title: "-debug (C# コンパイラ オプション) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /debug
dev_langs:
- CSharp
helpviewer_keywords:
- debug compiler option [C#]
- -debug compiler option [C#]
- /debug compiler option [C#]
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
caps.latest.revision: 19
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
ms.openlocfilehash: 6f22f998e4d652075e594c113026dfae18792ded
ms.contentlocale: ja-jp
ms.lasthandoff: 05/10/2017

---
# <a name="debug-c-compiler-options"></a>/debug (C# コンパイラ オプション)
**/debug** オプションを指定すると、コンパイラによってデバッグ情報が生成され、出力ファイルに格納されます。  
  
## <a name="syntax"></a>構文  
  
```console  
/debug[+ | -]  
/debug:{full | pdbonly}  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 `+` を指定するか、または単に **/debug** と指定すると、コンパイラによってデバッグ情報が生成され、その情報がプログラム データベース (.pdb ファイル) に出力されます。 **/debug** を指定しない場合、`-` の指定が有効となります。これを指定した場合、デバッグ情報は作成されません。  
  
 `full` &#124; `pdbonly`  
 コンパイラによって生成されるデバッグ情報の種類を指定します。 full 引数を使用すると (**/debug:pdbonly** を指定しない場合)、実行中のプログラムにデバッガーをアタッチできます。 pdbonly を指定すると、プログラムがデバッガーで開始されたときにはソース コードをデバッグできますが、実行中のプログラムをデバッガーにアタッチしたときはアセンブラーしか表示されません。  
  
## <a name="remarks"></a>コメント  
 このオプションを使用してデバッグ ビルドを作成します。 **/debug**、**/debug+**、または **/debug:full** のいずれも指定しなかった場合、プログラムの出力ファイルをデバッグすることはできません。  
  
 **/debug:full** を使用する場合は、JIT によって最適化されるコードの速度とサイズに若干影響が生じる点に注意してください。また、**/debug:full** でデバッグした場合、わずかではありますが、コードの品質にも影響が生じます。 生成されるリリース コードには、**/debug:pdbonly** を使用するか、PDB を一切使用しないことをお勧めします。  
  
> [!NOTE]
>  **/debug:pdbonly** と **/debug:full** の唯一の違いは、**/debug:full** でコンパイルした場合、デバッグ情報が利用可能であることを JIT コンパイラに通知するための <xref:System.Diagnostics.DebuggableAttribute> が生成される点です。 したがって、**/debug:full** を使用する場合に、コード内で <xref:System.Diagnostics.DebuggableAttribute> が false に設定されていると、エラーが生成されます。  
  
 アプリケーションのデバッグ パフォーマンスを構成する方法については、「[イメージのデバッグの簡略化](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md)」を参照してください。  
  
 .pdb ファイルの場所を変更する方法については、「[/pdb (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md)」を参照してください。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[ビルド]** プロパティ ページをクリックします。  
  
3.  **[詳細設定]** ボタンをクリックします。  
  
4.  **[デバッグ情報]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>」を参照してください。  
  
## <a name="example"></a>例  
 デバッグ情報を出力ファイル `app.pdb` に出力します。  
  
```console  
csc /debug /pdb:app.pdb test.cs  
```  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB 方法: プロジェクト プロパティと構成設定を変更する](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
