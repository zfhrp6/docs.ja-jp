---
title: "-checked (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /checked
dev_langs:
- CSharp
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: 20
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
ms.openlocfilehash: 63ba89ec42748ccea065bf0fd258fb559abca099
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="checked-c-compiler-options"></a>/checked (C# コンパイラ オプション)
**/checked** オプションは、データ型の範囲外の値になる整数の算術ステートメントと、[checked](../../../csharp/language-reference/keywords/checked.md) または [unchecked](../../../csharp/language-reference/keywords/unchecked.md) キーワードのスコープ内に含まれない整数の算術ステートメントで、ランタイム例外が発生するかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
/checked[+ | -]  
```  
  
## <a name="remarks"></a>コメント  
 `checked` または `unchecked` キーワードのスコープ内に含まれる整数の算術ステートメントは、**/checked** オプションの作用の対象になりません。  
  
 `checked` または `unchecked` キーワードのスコープ内に含まれない整数の算術ステートメントがデータ型の範囲外の値になり、**/checked+** (**/checked**) がコンパイル時に使用されている場合は、そのステートメントでランタイム例外が発生します。 **/checked-** がコンパイル時に使用された場合、そのステートメントでランタイム例外は発生しません。  
  
 このオプションの既定値は **/checked-** です。 **/checked-** を使用する 1 つのシナリオとして、大規模なアプリケーションをビルドする場合があります。 場合によって、このようなアプリケーションのビルドには自動化ツールが使用されます。そのようなツールで **/checked** が自動的に + に設定されることがあります。 **/checked-**を指定することにより、ツールのグローバルな既定値を無視することができます。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。 詳細については、「[Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)」([ビルド] ページ (プロジェクト デザイナー) (C#)) を参照してください。  
  
2.  **[ビルド]** プロパティ ページをクリックします。  
  
3.  **[詳細設定]** ボタンをクリックします。  
  
4.  **[演算のオーバーフローおよびアンダーフローのチェック]** プロパティを変更します。  
  
 プログラムによってこのコンパイラ オプションにアクセスする方法については、<xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A> に関する記事をご覧ください。  
  
## <a name="example"></a>例  
 次のコマンドは `t2.cs` をコンパイルします。 コマンドで使用されている `/checked` は、ファイル内の整数の算術ステートメントのうち、`checked` または `unchecked` キーワードのスコープ内に含まれず、データ型の範囲外の値になるステートメントで、ランタイム例外が発生することを指定します。  
  
```console  
csc t2.cs /checked  
```  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)   
 [プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)

