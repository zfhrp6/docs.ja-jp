---
title: "相互運用性の概要 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, 相互運用性"
  - "C++ 相互運用機能"
  - "COM 相互運用機能"
  - "相互運用性, 相互運用性の概要"
  - "プラットフォーム呼び出し"
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
caps.latest.revision: 43
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 43
---
# 相互運用性の概要 (C# プログラミング ガイド)
このトピックでは、C\# のマネージ コードとアンマネージ コードの間の相互運用を可能にする方法について説明します。  
  
## プラットフォーム呼び出し  
 *プラットフォーム呼び出し*は、マネージ コードから、たとえば Microsoft Win32 API の関数のような、ダイナミック リンク ライブラリ \(DLL\) に実装されたアンマネージ関数を呼び出すことができるようにするサービスです。  プラットフォーム呼び出しは、エクスポートされた関数を検索して呼び出し、必要に応じてその引数 \(整数、文字列、配列、構造体など\) をマーシャリングして、相互運用上の境界にまたがる動作を可能にします。  
  
 詳細については、「[アンマネージ DLL 関数の処理](../Topic/Consuming%20Unmanaged%20DLL%20Functions.md)」および「[方法: プラットフォーム呼び出しを使用して Wave ファイルを再生する](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)」を参照してください。  
  
> [!NOTE]
>  [共通言語ランタイム](../Topic/Common%20Language%20Runtime%20\(CLR\).md) \(CLR\) は、システム リソースへのアクセスを管理します。  CLR 外部のアンマネージ コードの呼び出しは、このセキュリティ機構をバイパスするため、セキュリティ上のリスクが生じます。  たとえば、アンマネージ コードは、アンマネージ コード内のリソースを直接呼び出し、CLR のセキュリティ機構をバイパスすることがあります。  詳細については、「[.NET Framework Security](http://go.microsoft.com/fwlink/?LinkId=37122)」を参照してください。  
  
## C\+\+ Interop  
 C\+\+ interop \(IJW \(It Just Works\) とも呼ばれる\) を使用すると、ネイティブ C\+\+ クラスをラップして、C\# またはその他の .NET Framework 言語で作成されたコードからそれらを利用できるようにすることができます。  そのためには、ネイティブ DLL コンポーネントまたは COM コンポーネントをラップする C\+\+ コードを記述します。  他の .NET Framework 言語とは異なり、[!INCLUDE[vcprvc](../../../csharp/programming-guide/interop/includes/vcprvc-md.md)] には相互運用性サポートが備えられています。これを利用すると、マネージ コードとアンマネージ コードが同じアプリケーション内に、さらには同じファイル内にも共存できるようになります。  その後、マネージ アセンブリを生成するスイッチを指定した **\/clr** コンパイラで、C\+\+ コードをビルドします。  最後に、アセンブリへの参照を C\# プロジェクトに追加し、ラップされたオブジェクトを、その他のマネージ クラスを使用するのと同じように使用します。  
  
## COM コンポーネントの C\# への公開  
 COM コンポーネントを C\# プロジェクトから使用できます。  基本的な手順は次のとおりです。  
  
1.  使用する COM コンポーネントを探して登録します。  regsvr32.exe を使用して登録するか、または COM DLL を登録解除します。  
  
2.  COM コンポーネントへの参照またはタイプ ライブラリをプロジェクトに追加します。  
  
     参照を追加すると、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] が [Tlbimp.exe \(タイプ ライブラリ インポーター\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md) を使用し、タイプ ライブラリを入力として受け取って .NET Framework 相互運用アセンブリを出力します。  アセンブリ \(ランタイム呼び出し可能ラッパー \(RCW\) とも呼ばれる\) には、タイプ ライブラリ内にある COM クラスとインターフェイスをラップするマネージ クラスとインターフェイスが含まれています。  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] は、生成されたアセンブリへの参照をプロジェクトに追加します。  
  
3.  RCW 内で定義されているクラスのインスタンスを作成します。  このインスタンスが、COM オブジェクトのインスタンスを作成します。  
  
4.  他のマネージ オブジェクトを使用するのとまったく同じようにこのオブジェクトを使用します。  ガベージ コレクションでオブジェクトが回収されると、COM オブジェクトのインスタンスもメモリから解放されます。  
  
 詳細については、「[.NET Framework への COM コンポーネントの公開](../Topic/Exposing%20COM%20Components%20to%20the%20.NET%20Framework.md)」を参照してください。  
  
## C\# の COM への公開  
 COM クライアントは、正しく公開されている C\# 型を使用できます。  C\# 型を公開する基本的な手順は、次のとおりです。  
  
1.  C\# プロジェクトに相互運用属性を追加します。  
  
     [!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)] プロジェクトのプロパティを変更して、アセンブリ COM を参照可能にします。  詳細については、「[\[アセンブリ情報\] ダイアログ ボックス](/visual-studio/ide/reference/assembly-information-dialog-box)」を参照してください。  
  
2.  COM タイプ ライブラリを生成し、それを COM 使用のために登録します。  
  
     [!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)] プロジェクトのプロパティを変更して、COM 相互運用用に C\# アセンブリを自動的に登録できます。  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] は、`/tlb` コマンド ライン スイッチを指定して、[Regasm.exe \(アセンブリ登録ツール\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md) を実行します。これにより、マネージ アセンブリが入力として受け取られ、タイプ ライブラリが生成されます。  このタイプ ライブラリは、アセンブリ内の `public` 型が記述されており、レジストリ エントリを追加して COM クライアントがマネージ クラスを作成できるようにします。  
  
 詳細については、「[COM への .NET Framework コンポーネントの公開](../Topic/Exposing%20.NET%20Framework%20Components%20to%20COM.md)」および「[COM クラスの例](../../../csharp/programming-guide/interop/example-com-class.md)」を参照してください。  
  
## 参照  
 [Improving Interop Performance](http://go.microsoft.com/fwlink/?LinkId=99564)   
 [Introduction to COM Interop](http://go.microsoft.com/fwlink/?LinkId=112406)   
 [Marshaling between Managed and Unmanaged Code](http://go.microsoft.com/fwlink/?LinkId=112398)   
 [アンマネージ コードとの相互運用](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Advanced COM Interoperability](http://msdn.microsoft.com/ja-jp/3ada36e5-2390-4d70-b490-6ad8de92f2fb)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)