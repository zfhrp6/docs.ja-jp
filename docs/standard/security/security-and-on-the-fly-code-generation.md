---
title: "セキュリティと実行時のコード生成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c6bb895979fb44616349505a07591f9ced9fedac
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="security-and-on-the-fly-code-generation"></a>セキュリティと実行時のコード生成
ライブラリによっては、コードを生成し、それを実行することによって、呼び出し元のためになんらかの処理を行います。 基本的に問題となるのは、より低い信頼度のコードの代わりに生成し、そのコードをより高い信頼度で実行することです。 呼び出し側がコードの生成に影響を及ぼすと問題はさらに悪化するため、安全と考えられるコードだけが生成されることを確認してください。  
  
 常に、どのようなコードが生成されているのかを知る必要があります。 これは、ユーザーから取得する値を厳しく制御することが必要であることを意味します。これらの値は、引用符で囲まれた文字列、ID、またはそれ以外です。引用符で囲まれた文字列は予期しないコード要素を含まないようにエスケープ処理が必要で、ID は有効な ID かどうかをチェックする必要があります。 コンパイルされたアセンブリは変更できるため、変更によってその ID に異常な文字が含まれると、セキュリティが脅かされます。このため、ID にも危険性があります。ただし、これがセキュリティ脆弱性になることは稀です。  
  
 リフレクション出力を指定してコードを生成することをお勧めします。これは、上記の多くの問題を防ぐのに役立ちます。  
  
 コードをコンパイルするときに、悪意のあるプログラムがなんらかの方法でコードを変更できるかどうかを考慮します。 コンパイラがソース コードを読み取る前、またはコードが .dll を読み込む前に、悪意のあるコードがソース コードを変更できる時間的なすきまがないかどうかを確認します。 ある場合は、ファイル システムのアクセス制御リストを適切に使用して、これらのファイルが格納されているディレクトリを保護する必要があります。  
  
## <a name="see-also"></a>参照  
 [安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)
