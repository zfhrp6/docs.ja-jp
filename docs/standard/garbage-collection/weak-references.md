---
title: "弱い参照"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 906c23caa7065486bb094ad2475ed9e7e24b3d9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="weak-references"></a>弱い参照
ガベージ コレクターでは、アプリケーションのコードがオブジェクトにアクセスできる間、そのアプリケーションで使用中のオブジェクトを収集することはできません。 アプリケーションには、オブジェクトへの強い参照があると考えられます。  
  
 弱い参照は、アプリケーションからオブジェクトへのアクセスを許容したまま、そのオブジェクトをガベージ コレクターが収集できるようにします。 弱い参照は、強い参照が存在しない場合に、オブジェクトが収集されるまでの不確定の期間中のみ有効です。 弱い参照を使用すると、該当オブジェクトが収集されるのを回避するため、アプリケーションで強い参照を取得できます。 ただし、強い参照が再確立される前に、ガベージ コレクターが最初にオブジェクトにアクセスするリスクが常にあります。  
  
 弱い参照は、多くのメモリを使用するが、ガベージ コレクションによって回収される場合、簡単に再作成できるオブジェクトに便利です。  
  
 たとえば、Windows フォーム アプリケーションでのツリー ビューでは、オプションの場合は、複雑な階層的な選択をユーザーに表示します。 基になるデータが大きければ、ユーザーがアプリケーションで他の操作を行っている場合、ツリーをメモリ内に保持しても効果的ではありません。  
  
 ユーザーは、アプリケーションの別の部分に切り替えて、ときに行うこともできます、<xref:System.WeakReference>クラスをツリーへの弱い参照を作成し、すべての強力な参照を破棄します。 ユーザーがツリーに戻ると、アプリケーションはツリーへの強い参照を取得しようとします。成功した場合、ツリーの再作成は回避されます。  
  
 作成するオブジェクトの弱い参照を確立するために、<xref:System.WeakReference>追跡対象となるオブジェクトのインスタンスを使用します。 設定して、<xref:System.WeakReference.Target%2A>にそのオブジェクトを設定し、オブジェクトへの参照を元のプロパティ`null`です。 コード例は、次を参照してください。<xref:System.WeakReference>クラス ライブラリです。  
  
## <a name="short-and-long-weak-references"></a>短期間と長期間の弱い参照  
 短期間の弱い参照または長期間の弱い参照を作成できます。  
  
-   Short  
  
     短期間の弱い参照の対象は、オブジェクトがガベージ コレクションによって回収されると、`null` になります。 弱い参照自体が管理オブジェクトであり、その他の管理オブジェクトと同じようにガベージ コレクションの対象です。  短いの弱い参照は、既定のコンス トラクター<xref:System.WeakReference>です。  
  
-   Long  
  
     長期間の弱い参照はオブジェクトの後に保持されます<xref:System.Object.Finalize%2A>メソッドが呼び出されました。 これにより、オブジェクトが再作成されることを許可しますが、オブジェクトの状態は予測不可能なままです。 長い参照を使用する指定`true`で、<xref:System.WeakReference>コンス トラクターです。  
  
     オブジェクトの型がない場合、<xref:System.Object.Finalize%2A>メソッド、短い弱い参照機能を適用および弱い参照は有効なターゲットが収集されるまでの実行がファイナライザーの後にいつ発生する可能性はします。  
  
 強い参照を確立し、再度オブジェクトを使用するキャスト、<xref:System.WeakReference.Target%2A>のプロパティ、<xref:System.WeakReference>オブジェクトの型にします。 場合、<xref:System.WeakReference.Target%2A>プロパティから返される`null`オブジェクトが収集済みです。 それ以外の場合、アプリケーションが強い参照を再取得するためにオブジェクトを使用して続行することができます。  
  
## <a name="guidelines-for-using-weak-references"></a>弱い参照を使用するためのガイドライン  
 終了処理後のオブジェクトの状態が予測できないため、長期間の弱い参照は必要な場合にのみ使用します。  
  
 ポインター自体が同程度の大きさか、より大きい場合があるため、小さなオブジェクトへの弱い参照を使用しないでください。  
  
 メモリ管理の問題への自動的な解決方法として、弱い参照を使用しないでください。 代わりに、アプリケーションのオブジェクトを処理するために、効果的なキャッシュ ポリシーを開発します。  
  
## <a name="see-also"></a>関連項目  
 [ガベージ コレクション](../../../docs/standard/garbage-collection/index.md)
