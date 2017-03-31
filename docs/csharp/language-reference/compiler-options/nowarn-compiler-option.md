---
title: "-nowarn (C# コンパイラ オプション) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nowarn
dev_langs:
- CSharp
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
caps.latest.revision: 24
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
ms.openlocfilehash: 34152b6e7247ac112bcc9c725402b8c9a5d631ed
ms.lasthandoff: 03/13/2017

---
# <a name="nowarn-c-compiler-options"></a>/nowarn (C# コンパイラ オプション)
**/nowarn** オプションを使用すると、コンパイラから警告が出力されないようにすることができます。 警告番号が複数ある場合は、コンマで区切ります。  
  
## <a name="syntax"></a>構文  
  
```  
/nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>引数  
 `number1`, `number2`  
 コンパイラで表示しないようにする警告番号。  
  
## <a name="remarks"></a>コメント  
 警告 ID の数値だけを指定します。 たとえば、CS0028 を抑制する場合は、`/nowarn:28` と指定します。  
  
 `/nowarn` に渡された警告番号が以前のリリースでは有効であったが、今はコンパイラから削除されている場合、コンパイラはその番号を自動的に無視します。 たとえば、CS0679 は Visual Studio .NET 2002 のコンパイラでは有効でしたが、その後削除されました。  
  
 `/nowarn` オプションでは、次の警告は抑制されません。  
  
-   コンパイラの警告 (レベル 1) CS2002  
  
-   コンパイラの警告 (レベル 1) CS2023  
  
-   コンパイラの警告 (レベル 1) CS2029  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。 詳細については、「[[ビルド] ページ (プロジェクト デザイナー) (C#)](https://docs.microsoft.com/visualstudio/ide/reference/build-page-project-designer-csharp)」を参照してください。  
  
2.  **[ビルド]** プロパティ ページをクリックします。  
  
3.  [**警告の表示なし**] プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.DelaySign%2A>」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB 方法: プロジェクト プロパティと構成設定を変更する](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [C# コンパイラ エラー](../../../csharp/language-reference/compiler-messages/index.md)
