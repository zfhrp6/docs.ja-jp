---
title: -nostdlib (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 1dc0ab70ca28626c4a3f505c13ec1d6f828a4b05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (C# コンパイラ オプション)
**-nostdlib** は、System 名前空間の全体を定義する mscorlib.dll がインポートされないようにします。  
  
## <a name="syntax"></a>構文  
  
```console  
-nostdlib[+ | -]  
```  
  
## <a name="remarks"></a>コメント  
 独自の System 名前空間およびオブジェクトを定義または作成する場合は、このオプションを使用します。  
  
 **-nostdlib** を指定しないと、**-nostdlib-** を指定したことと同じで、mscorlib.dll がプログラムにインポートされます。 **-nostdlib** を指定することは、**-nostdlib+** を指定することと同じです。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[ビルド]** プロパティ ページをクリックします。  
  
3.  **[詳細設定]** ボタンをクリックします。  
  
4.  **[mscorlib.dll を参照しない]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
