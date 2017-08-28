---
title: "-optimize (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /optimize
dev_langs:
- CSharp
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: 15
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
ms.openlocfilehash: 75a2b65c159e9adb0103765468182919ed6b0a23
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="optimize-c-compiler-options"></a>/optimize (C# コンパイラ オプション)
**/optimize** オプションは、コンパイラで実行する最適化を有効または無効にします。最適化を実行すると、出力ファイルのサイズが小さくなり、速度と効率が向上します。  
  
## <a name="syntax"></a>構文  
  
```console  
/optimize[+ | -]  
```  
  
## <a name="remarks"></a>コメント  
 **/optimize** は実行時にコードを最適化するように共通言語ランタイムに指示します。  
  
 既定では、最適化が無効になります。 **/optimize+** を指定して最適化を有効にします。  
  
 モジュールをアセンブリで使用するように作成する場合は、アセンブリと同じ **/optimize** 設定を使用します。  
  
 **/o** は **/optimize** の省略形です。  
  
 **/optimize** オプションと [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) オプションを結合することができます。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[ビルド]** プロパティ ページをクリックします。  
  
3.  **コードの最適化**プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>」をご覧ください。  
  
## <a name="example"></a>例  
 `t2.cs` をコンパイルしてコンパイラの最適化を有効にします。  
  
```console  
csc t2.cs /optimize  
```  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)

