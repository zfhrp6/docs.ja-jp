---
title: "-unsafe (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.assetid: fdb77ed9-da03-45bd-bb7f-250704da1bcc
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 146977522b400418a26f6a83e1a0ccdca8675bf9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="unsafe-c-compiler-options"></a>/unsafe (C# コンパイラ オプション)
**/unsafe** コンパイラ オプションは、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) キーワードを使用するコードをコンパイルできるようにします。  
  
## <a name="syntax"></a>構文  
  
```console  
/unsafe  
```  
  
## <a name="remarks"></a>コメント  
 アンセーフ コードの詳細については、「[アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)」を参照してください。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[ビルド]** プロパティ ページをクリックします。  
  
3.  **[アンセーフ コードの許可]** チェック ボックスをオンにします。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>」を参照してください。  
  
## <a name="example"></a>例  
 unsafe モードで `in.cs` をコンパイルする場合は、次のコードを使用します。  
  
```console  
csc /unsafe in.cs  
```  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)  
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
