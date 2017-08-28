---
title: "-baseaddress (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /dllbase
dev_langs:
- CSharp
helpviewer_keywords:
- baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
caps.latest.revision: 18
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
ms.openlocfilehash: 91193ae794957b5045a225614d6322e86d18d459
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="baseaddress-c-compiler-options"></a>/baseaddress (C# コンパイラ オプション)
**/baseaddress** オプションを使用すると、DLL を読み込む位置に推奨されるベース アドレスを指定できます。 このオプションを使用するタイミングと理由の詳細については、[アプリケーションの起動時間の短縮](http://go.microsoft.com/fwlink/?LinkId=107043)に関するページと、[Larry Osterman のブログ](http://go.microsoft.com/fwlink/?LinkId=107044)をご覧ください。  
  
## <a name="syntax"></a>構文  
  
```console  
/baseaddress:address  
```  
  
## <a name="arguments"></a>引数  
 `address`  
 DLL のベース アドレス。 このアドレスは、10 進数、16 進数、または 8 進数で指定できます。  
  
## <a name="remarks"></a>コメント  
 DLL の既定のベース アドレスは、.NET Framework 共通言語ランタイムにより設定されます。  
  
 このアドレスの下位ワードは丸められることに注意してください。 たとえば、0x11110001 と指定すると、丸められて 0x11110000 になります。  
  
 DLL の署名プロセスを完了するには、-R オプションを指定した SN.EXE を使用します。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[ビルド]** プロパティ ページをクリックします。  
  
3.  [詳細設定 **** ] ボタンをクリックします。  
  
4.  **DLL のベース アドレス** プロパティを変更します。  
  
     このコンパイラ オプションをプログラムによって設定するには、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=fullName>   
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)

