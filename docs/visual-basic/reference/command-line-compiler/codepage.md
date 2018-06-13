---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 383b6adae94c27efdd236de31ddfa8d16a6d4648
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648529"
---
# <a name="-codepage-visual-basic"></a>-codepage (Visual Basic)
コンパイルですべてのソース コード ファイルに使用するコード ページを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`id`|必須。 コンパイラによって指定されたコード ページを使用して`id`ソース ファイルのエンコーディングを解釈します。|  
  
## <a name="remarks"></a>コメント  
 使用することができます、特定のエンコードで保存されたソース コードをコンパイルする`-codepage`するコード ページを使用する必要がありますを指定します。 `-codepage`オプションは、コンパイル時にすべてのソース コード ファイルに適用されます。 詳細については、次を参照してください。 [.NET Framework の文字エンコーディング](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9)です。  
  
 `-codepage`シグネチャを持つ現在の ANSI コード ページ、Unicode または utf-8 を使用して、ソース コード ファイルを保存した場合、オプションは必要ありません。 Visual Studio に保存既定では、すべてのソース コード ファイルが現在の ANSI コード ページで、ユーザーで他のエンコーディングを指定しない限り、**エンコード** ダイアログ ボックス。 Visual Studio を使用して、**エンコード** ダイアログ ボックスを開くにはソース コード ファイルを別のコード ページを保存します。  
  
> [!NOTE]
>  `-codepage`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
