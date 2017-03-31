---
title: "-main (C# コンパイラ オプション) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /main
dev_langs:
- CSharp
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: 14
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fa8c02a6521b65e2cc4f7c8d779c1091ce399fba
ms.lasthandoff: 03/13/2017

---
# <a name="main-c-compiler-options"></a>/main (C# コンパイラ オプション)
このオプションは、**Main** メソッドを含むクラスが複数ある場合に、プログラムへのエントリ ポイントを含むクラスを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/main:class  
```  
  
## <a name="arguments"></a>引数  
 `class`  
 **Main** メソッドを含む型です。  
  
## <a name="remarks"></a>コメント  
 [Main](../../../csharp/programming-guide/main-and-command-args/index.md) メソッドを使用した型がコンパイル対象に 2 つ以上含まれている場合には、プログラムへのエントリ ポイントとして使用する **Main** メソッドがどの型に含まれているかを指定できます。  
  
 このオプションは、.exe ファイルをコンパイルする際に使用されます。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[アプリケーション]** プロパティ ページをクリックします。  
  
3.  **[スタートアップ オブジェクト]** プロパティを変更します。  
  
     このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.StartupObject%2A>」をご覧ください。  
  
## <a name="example"></a>例  
 **Main** メソッドが`Test2` にあることを指定して、`t2.cs` と `t3.cs` をコンパイルします。  
  
```  
csc t2.cs t3.cs /main:Test2  
```  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB 方法: プロジェクト プロパティと構成設定を変更する](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
