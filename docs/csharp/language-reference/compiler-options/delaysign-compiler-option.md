---
title: "-delaysign (C# コンパイラ オプション) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /delaysign
dev_langs:
- CSharp
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
caps.latest.revision: 16
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
ms.openlocfilehash: f3dc76214acb66f2212a3611c0c419889e58c359
ms.contentlocale: ja-jp
ms.lasthandoff: 05/10/2017

---
# <a name="delaysign-c-compiler-options"></a>/delaysign (C# コンパイラ オプション)
このオプションを使用すると、出力ファイルに署名用のスペースが予約され、デジタル署名を後で追加できるようになります。  
  
## <a name="syntax"></a>構文  
  
```console  
/delaysign[ + | - ]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 完全署名されたアセンブリを作成する場合は、**/delaysign-** を使用します。 アセンブリに公開キーだけを含める場合は、**/delaysign+** を使用します。 既定値は **/delaysign-** です。  
  
## <a name="remarks"></a>コメント  
 **/delaysign** オプションは、[/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) または [/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md) と共に使用しない場合、無効になります。  
  
 アセンブリに完全に署名するように指定すると、コンパイラはマニフェスト (アセンブリ メタデータ) を含むファイルをハッシュし、秘密キーでそのハッシュに署名します。 結果として得られるデジタル署名は、マニフェストを含むファイルに格納されます。 アセンブリを遅延署名に設定すると、コンパイラは署名の計算も格納も行いませんが、後で署名を追加できるようにファイルに領域を確保します。  
  
 たとえば、**/delaysign+** を指定すると、テスト時にはアセンブリをグローバル キャッシュに格納できます。 テスト後に、[アセンブリ リンカー](https://msdn.microsoft.com/library/c405shex) ユーティリティを使用してアセンブリに秘密キーを配置することにより、そのアセンブリに完全署名できます。  
  
 詳細については、「[厳密な名前付きアセンブリの作成と使用](https://msdn.microsoft.com/library/xwb8f617)」および「[アセンブリへの遅延署名](../../../framework/app-domains/delay-sign-assembly.md)」をご覧ください。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[遅延署名のみ]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.DelaySign%2A>」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB 方法: プロジェクト プロパティと構成設定を変更する](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
