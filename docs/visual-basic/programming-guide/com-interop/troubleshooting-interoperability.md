---
title: "Troubleshooting Interoperability (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "interop, deploying assemblies"
  - "assemblies [Visual Basic]"
  - "interop, installing assemblies that share components"
  - "COM objects, troubleshooting"
  - "interop, sharing components"
  - "troubleshooting interoperability"
  - "interoperability, troubleshooting"
  - "COM interop, troubleshooting"
  - "assemblies [Visual Basic], deploying"
  - "troubleshooting Visual Basic, interoperability"
  - "interop assemblies"
  - "interoperability, sharing components"
  - "shared components, using with assemblies"
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Troubleshooting Interoperability (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

COM オブジェクトと [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] のマネージ コードの間で相互運用するときには、以下のような一般的な問題が発生することがあります。  
  
##  <a name="vbconinteroperabilitymarshalinganchor1"></a> 相互運用マーシャリング  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] に含まれないデータ型を使用しなければならないケースも考えられます。  相互運用アセンブリは COM オブジェクトの大部分の操作を処理しますが、マネージ オブジェクトを COM に公開するときに、使用するデータ型を制御する必要が生じることもあります。  たとえば、クラス ライブラリ内の構造体では、Visual Basic 6.0 で作成された COM オブジェクトに送信される文字列に対して、`BStr` アンマネージ型を指定する必要があります。  そのような場合は、<xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性を使用して、マネージ型がアンマネージ型として公開されるように指定できます。  
  
##  <a name="vbconinteroperabilitymarshalinganchor2"></a> 固定長文字列のアンマネージ コードへのエクスポート  
 6.0 以前の Visual Basic では、文字列は null 終了文字のないバイト シーケンスとして COM オブジェクトにエクスポートされます。  [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] では、その他の言語との互換性を考慮して、文字列をエクスポートするときに終了文字が追加されます。  この非互換性の問題に対処する最善の方法は、終了文字のない文字列をバイト型 \(`Byte`\) または char 型 \(`Char`\) の配列としてエクスポートする方法です。  
  
##  <a name="vbconinteroperabilitymarshalinganchor3"></a> 継承階層のエクスポート  
 マネージ クラスの階層は、COM オブジェクトとして公開されるときに平坦化されます。  たとえば、メンバーを含む基本クラスを定義し、COM オブジェクトとして公開される派生クラス内でその基本クラスを継承すると、COM オブジェクト内の派生クラスを使用するクライアントは、継承されるメンバーを使用できなくなります。  基本クラスのメンバーに COM オブジェクトからアクセスできるのは、基本クラスのインスタンスとしてだけであり、その基本クラスも COM オブジェクトとして作成されている場合に限られます。  
  
## オーバーロードされたメソッド  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ではオーバーロードされたメソッドを作成できますが、COM ではオーバーロードされたメソッドはサポートされていません。  オーバーロードされたメソッドを含むクラスを COM オブジェクトとして公開した場合、オーバーロードされたメソッドに対して新しいメソッド名が生成されます。  
  
 たとえば、`Synch` メソッドについて、2 つのオーバーロードを持つクラスがあるとします。  このクラスを COM オブジェクトとして公開した場合、`Synch` と `Synch_2` というメソッド名が新たに生成されます。  
  
 COM オブジェクトのコンシューマーから見ると、この名前変更には 2 つの問題点があります。  
  
1.  クライアントが想定していないメソッド名が生成される可能性があります。  
  
2.  COM オブジェクトとして公開されたクラスまたはその基本クラスに新しいオーバーロードが追加された場合、いったん生成されたメソッド名が変わることがあります。  これにより、バージョン管理の問題が生じる可能性があります。  
  
 この 2 つの問題を解決するには、COM オブジェクトとして公開されるオブジェクトを開発するときに、オーバーロードの使用を避け、各メソッドに一意の名前を指定するようにします。  
  
##  <a name="vbconinteroperabilitymarshalinganchor4"></a> 相互運用アセンブリを通じた COM オブジェクトの使用  
 相互運用アセンブリは、それらが表す COM オブジェクトに置き換わるマネージ コードとして使用します。  ただし、相互運用アセンブリはラッパーであり、実際の COM オブジェクトではないため、相互運用アセンブリと標準アセンブリの使用には多少の違いがあります。  相違点としては、クラスの公開、パラメーターおよび戻り値のデータ型などがあります。  
  
##  <a name="vbconinteroperabilitymarshalinganchor5"></a> インターフェイスおよびクラスとして公開されるクラス  
 COM クラスは、標準アセンブリのクラスとは異なり、COM クラスを表すインターフェイスおよびクラスの両方として相互運用アセンブリで公開されます。  インターフェイスの名前は COM クラスの名前と同じです。  相互運用クラスの名前は元の COM クラスと同じですが、"Class" という語が末尾に追加されます。  たとえば、COM オブジェクトの相互運用アセンブリへの参照を持つプロジェクトがあるとします。  COM クラスの名前が `MyComClass` である場合、IntelliSense およびオブジェクト ブラウザーには、`MyComClass` という名前のインターフェイスと `MyComClassClass` という名前のクラスが表示されます。  
  
##  <a name="vbconinteroperabilitymarshalinganchor6"></a> .NET Framework クラスのインスタンスの作成  
 通常、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] クラスのインスタンスを作成するときは、`New` ステートメントとクラス名を使用します。  相互運用アセンブリによって表される COM クラスを持つということは、`New` ステートメントとインターフェイスを使用できる 1 つのケースです。  COM クラスと `Inherits` ステートメントを使用する場合を除いて、インターフェイスはクラスと同様に使用できます。  次のコードは、`Command` オブジェクトを、Microsoft ActiveX データ オブジェクト 2.8 ライブラリの COM オブジェクトへの参照があるプロジェクト内で作成する方法を示します。  
  
 [!code-vb[VbVbalrInterop#20](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_1.vb)]  
  
 ただし、COM クラスを派生クラスの基本クラスとして使用する場合は、COM クラスを表す相互運用クラスを使用する必要があります。次に例を示します。  
  
 [!code-vb[VbVbalrInterop#21](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_2.vb)]  
  
> [!NOTE]
>  相互運用機能アセンブリは、COM クラスを表すインターフェイスを暗黙的に実装します。  `Implements` ステートメントを使用してこれらのインターフェイスを実装しないでください。エラーが発生します。  
  
##  <a name="vbconinteroperabilitymarshalinganchor7"></a> パラメーターおよび戻り値のデータ型  
 標準アセンブリのメンバーと異なり、相互運用機能アセンブリのメンバーは、オブジェクトの元の宣言で使用されているデータ型とは異なるデータ型を持つ場合があります。  相互運用アセンブリは COM 型を互換性のある共通言語ランタイム型に暗黙的に変換しますが、実行時エラーが発生しないように、両側で使用されるデータ型に注意する必要があります。  たとえば、Visual Basic 6.0 以前で作成された COM オブジェクトでは、整数型 \(`Integer`\) の値に、対応する [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] の短整数型 \(`Short`\) が使用されます。  インポートしたメンバーを使用する場合は、オブジェクト ブラウザーでその特性を調べてから使用することをお勧めします。  
  
##  <a name="vbconinteroperabilitymarshalinganchor8"></a> モジュール レベルの COM メソッド  
 ほとんどの COM オブジェクトは、`New` キーワードを使用して COM クラスのインスタンスを作成し、そのオブジェクトのメソッドを呼び出すことによって使用されます。  この規則の例外としては、`AppObj` または `GlobalMultiUse` COM クラスを含む COM オブジェクトがあります。  このようなクラスは、[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] のクラスのモジュール レベルのメソッドと似ています。  Visual Basic 6.0 以前のバージョンでは、このようなオブジェクトのメソッドのいずれかを最初に呼び出したときに、インスタンスが暗黙的に作成されます。  たとえば、Visual Basic 6.0 では、最初にインスタンスを作成しなくても、Microsoft DAO 3.6 オブジェクト ライブラリへの参照を追加し、`DBEngine` メソッドを呼び出すことができます。  
  
```  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] では、必ず COM オブジェクトのインスタンスを作成してから、これらのメソッドを使用する必要があります。  [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] でこれらのメソッドを使用するには、目的のクラスの変数を宣言し、New キーワードを使用して、オブジェクト変数にオブジェクトを割り当てます。  クラスのインスタンスが 1 つだけ作成されていることを確認するときには、`Shared` キーワードを使用できます。  
  
 [!code-vb[VbVbalrInterop#23](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_3.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor9"></a> イベント ハンドラーで処理されないエラー  
 相互運用の一般的な問題の 1 つに、COM オブジェクトが発生したイベントを処理するイベント ハンドラーのエラーがあります。  `On Error` ステートメントまたは `Try...Catch...Finally` ステートメントを使用してエラーを明確にチェックしない限り、このようなエラーは無視されます。  次の例は Microsoft ActiveX データ オブジェクト 2.8 ライブラリの COM オブジェクトへの参照を含む [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] プロジェクトの一部です。  
  
 [!code-vb[VbVbalrInterop#24](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_4.vb)]  
  
 この例のコードは、エラーが通知されるように記述されています。  しかし、`Try...Catch...Finally` ブロックを使用せずにこのコードを実行すると、`OnError Resume Next` ステートメントを使用した場合と同じようにエラーが無視されます。  エラー処理がなければ、ゼロによる除算は通知なしで失敗します。  この種のエラーが未処理の例外エラーとして通知されることはないため、COM オブジェクトからのイベントを処理するイベント ハンドラーで例外処理の手段を講じることが重要です。  
  
### COM 相互運用エラーについて  
 相互運用の呼び出しでは、エラー処理を組み込んでいないと、エラーが発生してもそれに関する情報がほとんど得られません。  可能な場合は、必ず構造化されたエラー処理を使用して、エラー発生時の問題に関する情報が通知されるようにしてください。  これは、特にアプリケーションをデバッグするときに役立ちます。  次に例を示します。  
  
 [!code-vb[VbVbalrInterop#25](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_5.vb)]  
  
 例外オブジェクトの内容を調べることにより、エラーの説明 \(HRESULT\) や、COM エラーのソースなどの情報が得られます。  
  
##  <a name="vbconinteroperabilitymarshalinganchor10"></a> ActiveX コントロールの問題  
 Visual Basic 6.0 で動作するほとんどの ActiveX コントロールは、[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] でも問題なく動作します。  主な例外としては、コンテナー コントロール、つまり別のコントロールを視覚的に含むようなコントロールがあります。  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] で正常に動作しない古いコントロールの例は、次のとおりです。  
  
-   Microsoft Forms 2.0 フレーム コントロール  
  
-   スピン コントロールとも呼ばれるアップダウン コントロール  
  
-   Sheridan タブ コントロール  
  
 サポートされていない ActiveX コントロールに関する問題の回避方法はいくつかしかありません。  元のソース コードがある場合は、既存のコントロールを [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] に移行できます。  元のソース コードがない場合は、ソフトウェアの販売元に問い合わせて、サポートされていない ActiveX コントロールを、更新された .NET 互換バージョンのコントロールに置き換えてください。  
  
##  <a name="vbconinteroperabilitymarshalinganchor11"></a> ByRef を使用した、コントロールの ReadOnly プロパティの受け渡し  
 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] では、古い ActiveX コントロールの `ReadOnly` プロパティを `ByRef` パラメーターとして別のプロシージャに渡すときに、"Error 0x800A017F CTL\_E\_SETNOTSUPPORTED" などの COM エラーが発生することがあります。  Visual Basic 6.0 では、同様にプロシージャを呼び出してもエラーは発生せず、パラメーターは値で渡す場合と同様に扱われます。  [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] では、Property `Set` プロシージャを持たないプロパティを変更しようとしているという内容のエラー メッセージが COM オブジェクトとして表示されます。  
  
 呼び出し先のプロシージャにアクセスできる場合は、`ByVal` キーワードを使用して `ReadOnly` プロパティを受け入れるパラメーターを宣言することにより、このエラーを阻止できます。  次に例を示します。  
  
 [!code-vb[VbVbalrInterop#26](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_6.vb)]  
  
 呼び出し先のプロシージャのソース コードにアクセスできない場合は、呼び出し元プロシージャをさらにかっこで囲むことにより、プロパティを強制的に値で渡すことができます。  たとえば、Microsoft ActiveX データ オブジェクト 2.8 ライブラリの COM オブジェクトへの参照を含むプロジェクトでは、次のように指定できます。  
  
 [!code-vb[VbVbalrInterop#27](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_7.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor12"></a> 相互運用機能を公開するアセンブリの配置  
 COM インターフェイスを公開するアセンブリの配置については、いくつかの考慮事項があります。  たとえば、別のアプリケーションが同じ COM アセンブリを参照する場合、問題が発生する可能性があります。  このような状況として一般的なのは、新しいバージョンのアセンブリをインストールした後、別のアプリケーションが依然として古いバージョンのアセンブリを使用している場合です。  同じ DLL を共有するアセンブリのいずれかをアンインストールすると、他のアセンブリでその DLL が使用できなくなる可能性があります。  
  
 この問題を回避するには、各共有アセンブリをグローバル アセンブリ キャッシュ \(GAC: Global Assembly Cache\) にインストールし、そのコンポーネントに対して MergeModule を使用します。  アプリケーションを GAC にインストールできない場合は、バージョン固有のサブディレクトリにある CommonFilesFolder にインストールします。  
  
 共有されないアセンブリは、呼び出し元のアプリケーションと同じディレクトリに格納してください。  
  
## 参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Tlbimp.exe \(タイプ ライブラリ インポーター\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)   
 [Tlbexp.exe \(タイプ ライブラリ エクスポーター\)](../Topic/Tlbexp.exe%20\(Type%20Library%20Exporter\).md)   
 [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [グローバル アセンブリ キャッシュ](../Topic/Global%20Assembly%20Cache.md)