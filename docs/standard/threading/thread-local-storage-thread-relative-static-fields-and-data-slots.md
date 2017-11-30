---
title: "スレッド ローカル ストレージ : スレッド相対静的フィールドとデータ スロット"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], local storage
- threading [.NET Framework], thread-relative static fields
- local thread storage
- TLS
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 39dd80d378171563f2aadadaa146278e8a417d32
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>スレッド ローカル ストレージ : スレッド相対静的フィールドとデータ スロット
マネージ スレッド ローカル ストレージ (TLS) データを格納するスレッドおよびアプリケーション ドメインに一意であるを使用することができます。 .NET Framework には 2 つの方法を使用するマネージ TLS: スレッド相対静的フィールドとデータ スロット。  
  
-   スレッド相対静的フィールドを使用して (スレッド相対`Shared`Visual Basic でのフィールド) コンパイル時にニーズに正確に予測できる場合です。 スレッド相対静的フィールドは、最高のパフォーマンスを提供します。 コンパイル時の型チェックの利点も提供します。  
  
-   実際の要件は実行時にしか検出される可能性がありますとデータ スロットを使用します。 データ スロットは、速度は遅くなりにくいという、スレッド相対静的フィールドよりも使用して、データ型として格納されます<xref:System.Object>ので、使用する前に、正しい型にキャストする必要があります。  
  
 使用するアンマネージ C++ で`TlsAlloc`スロットを動的に割り当てると`__declspec(thread)`スレッド相対ストレージで変数を割り当てる必要があることを宣言します。 スレッド相対静的フィールドとデータ スロットは、この動作の管理対象のバージョンを提供します。  
  
 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]、使用することができます、<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>オブジェクトが最初に使用された場合に遅れて初期化されるスレッド ローカル オブジェクトを作成するクラス。 詳細については、「[限定的な初期化](../../../docs/framework/performance/lazy-initialization.md)」を参照してください。  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>管理されている TLS でのデータの一意性  
 スレッド相対静的フィールドまたはデータ スロットを使用するかどうかは、管理されている TLS でのデータをスレッドおよびアプリケーション ドメインの組み合わせに一意です。  
  
-   アプリケーション ドメイン内で 1 つのスレッドは両方のスレッドが同じフィールドまたはスロットを使用する場合でも、別のスレッドからのデータを変更できません。  
  
-   スレッドには、複数のアプリケーション ドメインからの同じフィールドまたはスロットがアクセスする、アプリケーション ドメインごとに別個の値が保持されます。  
  
 たとえば、スレッドの設定、スレッド相対静的フィールドの値が別のアプリケーション ドメインに入るし、フィールドの値を取得し、2 つ目のアプリケーション ドメインで取得した値は、最初のアプリケーション ドメインの値によって異なります。 2 つ目のアプリケーション ドメインで、フィールドの新しい値を設定しても、最初のアプリケーション ドメインにあるフィールドの値には影響しません。  
  
 同様に、スレッドは、次の 2 つの異なるアプリケーション ドメインで同じ名前付きデータ スロットを取得、ときに最初のアプリケーション ドメイン内のデータは、2 つ目のアプリケーション ドメイン内のデータの独立したままです。  
  
## <a name="thread-relative-static-fields"></a>スレッド相対静的フィールド  
 データの一部が一意でスレッドおよびアプリケーション ドメインの組み合わせを常にある場合は、適用、<xref:System.ThreadStaticAttribute>静的フィールドに属性します。 その他の静的フィールドで使用すると、フィールドを使用します。 フィールドのデータは、それを使用する各スレッドに固有です。  
  
 スレッド相対静的フィールドは、データ スロットよりもパフォーマンスが向上して、コンパイル時の型チェックの利点があります。  
  
 すべてのクラス コンス トラクター コード フィールドにアクセスする最初のコンテキストの最初のスレッドで実行されるに注意してください。 他のすべてのスレッドまたは同じアプリケーション ドメイン内のコンテキストで、フィールドが初期化する`null`(`Nothing` Visual Basic で) かどうかは、参照型ではまたはしている場合の値の型の値、既定値にします。 そのため、クラス コンス トラクターを使用してスレッド相対静的フィールドを初期化しないでください。 代わりに、初期化回避スレッド相対静的フィールドと仮定に初期化されます`null`(`Nothing`) または既定値にします。  
  
## <a name="data-slots"></a>データ スロット  
 .NET Framework では、スレッドおよびアプリケーション ドメインの組み合わせに固有の動的なデータ スロットを提供します。 データ スロットの 2 種類があります: スロット、および名前のないスロットをという名前です。 使用して実装されます両方、<xref:System.LocalDataStoreSlot>構造体。  
  
-   名前付きデータ スロットを作成するには、使用、<xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType>または<xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>メソッドです。 既存の名前付きのスロットへの参照を取得するには、自分の名前を渡します、<xref:System.Threading.Thread.GetNamedDataSlot%2A>メソッドです。  
  
-   無名のデータ スロットを作成するには、使用、<xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType>メソッドです。  
  
 という名前し、スロットの名前の両方を使用して、<xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType>と<xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType>設定して、スロット内の情報を取得するメソッド。 これらは、常に実行されているスレッドのデータを操作する静的メソッドです。  
  
 名前付きスロットは便利、その名前を渡すことによって必要なときに、スロットを取得できるため、<xref:System.Threading.Thread.GetNamedDataSlot%2A>メソッドの名前のないスロットへの参照を維持するのではなく、します。 ただし、別のコンポーネントがそのスレッド相対ストレージに対して同じ名前を使用して、スレッド コンポーネントとその他のコンポーネントの両方からコードを実行する場合は、2 つのコンポーネントにそれぞれのデータが破損している可能性があります。 (このシナリオでは、両方のコンポーネントが、同じアプリケーション ドメインで実行されていることと同じデータを共有するが設計されていません。)  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ContextStaticAttribute>  
 <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>  
 <xref:System.ThreadStaticAttribute>  
 <xref:System.Runtime.Remoting.Messaging.CallContext>  
 [スレッド化](../../../docs/standard/threading/index.md)
