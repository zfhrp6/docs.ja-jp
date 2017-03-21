---
title: "/moduleassemblyname |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f6b042b26ad866f177158562653c91f4f7527c04
ms.lasthandoff: 03/13/2017

---
# <a name="moduleassemblyname"></a>/target
このモジュールが一部となるアセンブリの名前を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`assembly_name`|このモジュールの一部となるアセンブリの名前。|  
  
## <a name="remarks"></a>コメント  
 コンパイラ プロセス、`/moduleassemblyname`場合にのみ、オプション、`/target:module`オプションを指定します。 モジュールを作成するコンパイラに対応します。 コンパイラによって作成されたモジュールがで指定されたアセンブリに対してのみ有効ですが、`/moduleassemblyname`オプション。 別のアセンブリでモジュールを配置する場合は、実行時エラーが発生します。  
  
 `/moduleassemblyname`オプションは、次に該当する場合にのみ必要があります。  
  
-   モジュール内のデータ型へのアクセスを必要な`Friend`参照先アセンブリの型。  
  
-   参照アセンブリは、モジュールをビルドするアセンブリにフレンド アセンブリのアクセス許可を与えします。  
  
 モジュールの作成の詳細については、次を参照してください。 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)します。 フレンド アセンブリの詳細については、次を参照してください。[フレンド アセンブリ](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)します。  
  
> [!NOTE]
>  `/moduleassemblyname`オプションは、Visual Studio 開発環境内から使用できません。 は、コマンド プロンプトからコンパイルする場合のみです。  
  
## <a name="see-also"></a>関連項目  
 [方法: マルチファイル アセンブリをビルド](http://msdn.microsoft.com/library/261c5583-8a76-412d-bda7-9b8ee3b131e5)   
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [/main](../../../visual-basic/reference/command-line-compiler/main.md)   
 [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)   
 [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [フレンド アセンブリ](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)
