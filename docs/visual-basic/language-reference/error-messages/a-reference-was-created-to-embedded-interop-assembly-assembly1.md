---
title: "参照が埋め込まれた相互運用機能アセンブリ &#39; に作成されました&lt;assembly1&gt;&#39;アセンブリ &#39; からそのアセンブリへの間接参照のため、;&lt;assembly2&gt;&#39;です。"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bc2fbb044fc839aa24abf3dc1ea864457efb0653
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-39ltassembly1gt39-because-of-an-indirect-reference-to-that-assembly-from-assembly-39ltassembly2gt39"></a>参照が埋め込まれた相互運用機能アセンブリ &#39; に作成されました&lt;assembly1&gt;&#39;アセンブリ &#39; からそのアセンブリへの間接参照のため、;&lt;assembly2&gt;&#39;です。
埋め込まれた相互運用機能アセンブリ '\<assembly1>' への参照が作成されました。これは、そのアセンブリへの間接参照がアセンブリ '\<assembly2>' によって作成されたためです。 両方のアセンブリで '相互運用機能型の埋め込み' プロパティを変更することを検討してください。  
  
 `Embed Interop Types` プロパティが `True` に設定されたアセンブリ (assembly1) に参照を追加しました。 これにより、コンパイラは、このアセンブリから相互運用機能の型情報を埋め込むよう指示されます。 ただし、参照していた別のアセンブリ (assembly2) もこのアセンブリ (assembly1) を参照しており、また `Embed Interop Types` プロパティが `False` に設定されているため、コンパイラはこのアセンブリから相互運用機能の型情報を埋め込むことができません。  
  
> [!NOTE]
>  アセンブリ参照の `Embed Interop Types` プロパティを `True` に設定することは、コマンド ライン コンパイラの `/link` オプションを使用してアセンブリを参照することと同じです。  
  
 **エラー ID:** BC40059  
  
### <a name="to-address-this-warning"></a>この警告に対処するには  
  
-   両方のアセンブリに相互運用の型情報を埋め込むには、assembly1 へのすべての参照の `Embed Interop Types` プロパティを `True` に設定します。  
  
-   assembly1 の `Embed Interop Types` プロパティを `False` に設定すると警告を回避できます。 この例では、相互運用機能型の詳細については、プライマリ相互運用機能アセンブリ (PIA) によって提供されます。  
  
## <a name="see-also"></a>関連項目  
 [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)  
 [プライマリ相互運用機能アセンブリを使ったプログラミング](http://msdn.microsoft.com/en-us/306fa1d6-0703-4004-9e93-d0a57f1be81e)
