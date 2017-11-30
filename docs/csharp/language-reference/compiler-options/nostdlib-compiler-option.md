---
title: "-nostdlib (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad3ca7775512623de43c7fe6b7fe1cf481ccca87
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="nostdlib-c-compiler-options"></a>/nostdlib (C# コンパイラ オプション)
**/nostdlib** は、System 名前空間の全体を定義する mscorlib.dll がインポートされないようにします。  
  
## <a name="syntax"></a>構文  
  
```console  
/nostdlib[+ | -]  
```  
  
## <a name="remarks"></a>コメント  
 独自の System 名前空間およびオブジェクトを定義または作成する場合は、このオプションを使用します。  
  
 **/nostdlib**を指定しないと、 **/nostdlib-**を指定したことと同じで、mscorlib.dll がプログラムにインポートされます。 **/nostdlib** を指定することは、 **/nostdlib+**を指定することと同じです。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[ビルド]** プロパティ ページをクリックします。  
  
3.  **[詳細設定]** ボタンをクリックします。  
  
4.  **[mscorlib.dll を参照しない]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
