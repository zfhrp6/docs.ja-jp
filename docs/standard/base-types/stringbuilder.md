---
title: ".NET における StringBuilder クラスの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Remove method
- strings [.NET Framework], capacities
- StringBuilder object
- Replace method
- AppendFormat method
- Append method
- Insert method
- strings [.NET Framework], StringBuilder object
ms.assetid: 5c14867c-9a99-45bc-ae7f-2686700d377a
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3a6c8f6dee9f2a1da6ed4a8219c1b4832464d9aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-stringbuilder-class-in-net"></a>.NET における StringBuilder クラスの使用
<xref:System.String>オブジェクトは変更できません。 内のメソッドのいずれかを使用するたびに、<xref:System.String?displayProperty=nameWithType>クラス、その新しいオブジェクトに対して、新しい使用領域の割り当てを必要とするメモリ内に新しい文字列オブジェクトを作成します。 新規作成に伴うオーバーヘッドを文字列に繰り返しの変更を実行する必要がある場合、<xref:System.String>オブジェクトはコストが高くなることができます。 <xref:System.Text.StringBuilder?displayProperty=nameWithType>クラスは、新しいオブジェクトを作成せずに文字列を変更する場合に使用できます。 たとえばを使用して、<xref:System.Text.StringBuilder>クラスは、ループで多数の文字列を連結するときのパフォーマンスを向上できます。  
  
## <a name="importing-the-systemtext-namespace"></a>System.Text 名前空間のインポート  
 <xref:System.Text.StringBuilder>クラスに存在、<xref:System.Text>名前空間。  コードで完全修飾型名を指定することを避けるため、インポートすることができます、<xref:System.Text>名前空間。  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>StringBuilder オブジェクトのインスタンス化  
 新しいインスタンスを作成することができます、<xref:System.Text.StringBuilder>クラスを次の例に示すように、オーバー ロードされたコンス トラクター メソッドの 1 つで変数を初期化します。  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>容量と長さの設定  
 ただし、<xref:System.Text.StringBuilder>をカプセル化される文字列の文字数を拡張できるようにする動的オブジェクトは、保持可能な文字の最大数の値を指定することができます。 この値は、オブジェクトの容量が呼び出され、文字列の長さと混同しないでを現在<xref:System.Text.StringBuilder>を保持します。 たとえばの新しいインスタンスを作成する場合があります、<xref:System.Text.StringBuilder>文字列「こんにちは」は、長さが 5 のクラスが、オブジェクトが最大容量として 25 に含まれているを指定する場合があります。 変更する場合、 <xref:System.Text.StringBuilder>、これによって再配置のサイズ自体の容量に達するまでします。 容量に達すると、新しい領域が自動的に割り当てられ、容量が 2 倍になります。 容量を指定することができます、<xref:System.Text.StringBuilder>クラスのオーバー ロードされたコンス トラクターのいずれかを使用します。 次の例は、`MyStringBuilder` オブジェクトを最大 25 の領域に拡張できることを示しています。  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 さらに、読み取り/書き込みを行うこともできます<xref:System.Text.StringBuilder.Capacity%2A>プロパティをオブジェクトの最大長を設定します。 次の例では、**Capacity** プロパティを使用して、オブジェクトの最大長を定義しています。  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 <xref:System.Text.StringBuilder.EnsureCapacity%2A>を現在の容量を確認するメソッドを使用できます**StringBuilder**です。 容量が渡された値よりも大きい場合、変更は行われません。しかし、容量が渡された値より小さい場合は、渡された値と一致するよう現行の容量が変更されます。  
  
 <xref:System.Text.StringBuilder.Length%2A>プロパティも表示または設定します。 **Length** プロパティを、**Capacity** プロパティより大きな値に設定する場合、**Capacity** プロパティは **Length** プロパティと同じ値に自動的に変更されます。 **Length** プロパティを、現行の **StringBuilder** 内の文字列の長さより小さい値に設定すると、文字列は短縮されます。  
  
## <a name="modifying-the-stringbuilder-string"></a>StringBuilder 文字列の変更  
 **StringBuilder** の内容の変更に使用できるメソッドを次の表に一覧表示します。  
  
|メソッド名|用途|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|現行の **StringBuilder** の末尾に情報を追加します。|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|文字列に渡される書式指定子を、書式設定されたテキスト文字列で置き換えます。|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|現行の **StringBuilder** の指定されたインデックスに、文字列またはオブジェクトを挿入します。|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|現行の **StringBuilder** から、指定された文字数を削除します。|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|指定されたインデックスで、指定された文字を置き換えます。|  
  
### <a name="append"></a>追加  
 **Append**現在によって表される文字列の末尾にテキストまたはオブジェクトの文字列表現を追加するメソッドを使用できます**StringBuilder**です。 次の例では、**StringBuilder** を "Hello World" に初期設定し、テキストをオブジェクトの末尾に追加しています。 領域は、必要に応じて自動的に割り当てられます。  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>AppendFormat  
 <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>メソッドの末尾にテキストを追加する、<xref:System.Text.StringBuilder>オブジェクト。 複合書式指定機能をサポートしています (詳細については、次を参照してください。[複合書式指定](../../../docs/standard/base-types/composite-formatting.md)) を呼び出して、<xref:System.IFormattable>以上の書式設定するオブジェクトの実装です。 そのため、数値、日時、および列挙の値に対して標準書式文字列を受け取り、数値と日時の値、およびカスタム型に定義されている書式文字列に対してカスタム書式文字列を受け取ります。 (書式設定については、「[型の書式設定](../../../docs/standard/base-types/formatting-types.md)」を参照してください。)このメソッドを使用して変数の形式をカスタマイズし、それらの値を追加することができます、<xref:System.Text.StringBuilder>です。 次の例では、<xref:System.Text.StringBuilder.AppendFormat%2A>の最後に、通貨値として書式設定された整数値を配置する方法、<xref:System.Text.StringBuilder>オブジェクト。  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>挿入  
 <xref:System.Text.StringBuilder.Insert%2A>メソッドは、現在の指定した位置に文字列型またはオブジェクトを追加します。<xref:System.Text.StringBuilder>オブジェクト。 次の例では、このメソッドを使用の 6 番目の位置に単語を挿入する、<xref:System.Text.StringBuilder>オブジェクト。  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>削除  
 使用することができます、**削除**現在から指定数の文字を削除する方法<xref:System.Text.StringBuilder>オブジェクト、指定した 0 から始まるインデックス位置を開始します。 次の例では、**削除**を短縮する方法、<xref:System.Text.StringBuilder>オブジェクト。  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>置換  
 **置換**内の文字を置換するメソッドを使用することができます、<xref:System.Text.StringBuilder>オブジェクトと別の指定した文字。 次の例では、**置換**を検索するメソッド、<xref:System.Text.StringBuilder>オブジェクトの感嘆符のすべてのインスタンスの文字 (!)、疑問符 (?) 文字 (?) に置き換えます。  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>文字列への StringBuilder オブジェクトの変換  
 変換する必要があります、<xref:System.Text.StringBuilder>オブジェクトを<xref:System.String>オブジェクトで表される文字列を渡す前に、<xref:System.Text.StringBuilder>オブジェクトを持つメソッドを<xref:System.String>パラメーターまたはユーザー インターフェイスに表示します。 この変換を行うには呼び出すことによって、<xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType>メソッドです。 次の例ではさまざまな<xref:System.Text.StringBuilder>メソッドを呼び出し、続いて、<xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType>文字列を表示するメソッド。  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Text.StringBuilder?displayProperty=nameWithType>  
 [基本的な文字列操作](../../../docs/standard/base-types/basic-string-operations.md)  
 [型の書式設定](../../../docs/standard/base-types/formatting-types.md)
