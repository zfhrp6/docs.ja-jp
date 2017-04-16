---
title: "方法 : アプリケーション スコープのリソース ディクショナリを使用する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アプリケーション スコープのリソース ディクショナリ"
  - "ディクショナリ, リソース"
  - "リソース ディクショナリ, アプリケーション スコープ"
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : アプリケーション スコープのリソース ディクショナリを使用する
この例では、アプリケーション スコープのカスタム リソース ディクショナリを定義および使用する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Application> は、共有リソースのアプリケーション スコープのストアである <xref:System.Windows.Application.Resources%2A> を公開します。  既定では、<xref:System.Windows.Application.Resources%2A> プロパティは、<xref:System.Windows.ResourceDictionary> 型のインスタンスで初期化されます。  このインスタンスは、<xref:System.Windows.Application.Resources%2A> を使用してアプリケーション スコープのプロパティを取得および設定する場合に使用します。  \(詳細については、「[How to: Get and Set an Application\-Scope Resource](http://msdn.microsoft.com/ja-jp/39e0420c-c9fc-47dc-8956-fdd95b214095)」を参照してください\)。  
  
 <xref:System.Windows.Application.Resources%2A> を使用して設定したリソースが複数ある場合は、カスタム リソース ディクショナリを使用してこれらのリソースを格納し、<xref:System.Windows.Application.Resources%2A> を設定することができます。  次に示すのは、XAML を使用してカスタム リソース ディクショナリを宣言する方法です。  
  
 [!code-xml[HOWTOResourceDictionaries#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 <xref:System.Windows.Application.Resources%2A> を使用してリソース ディクショナリ全体を交換することで、各テーマが単一のリソース ディクショナリでカプセル化されているアプリケーション スコープのテーマをサポートすることができます。  <xref:System.Windows.ResourceDictionary> を設定する方法を次の例に示します。  
  
 [!code-xml[HOWTOResourceDictionaries#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 次に示すのは、XAML の <xref:System.Windows.Application.Resources%2A> で公開されたリソース ディクショナリから、アプリケーション スコープのリソースを取得する方法です。  
  
 [!code-xml[HOWTOResourceDictionaries#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 次に示すのは、コードでリソースを取得する方法です。  
  
 [!code-csharp[HOWTOResourceDictionaries#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 <xref:System.Windows.Application.Resources%2A> を使用するときに注意すべき点が 2 つあります。  1 つ目は、ディクショナリ キーはオブジェクトであるため、プロパティ値を設定および取得するときに、まったく同じオブジェクト インスタンスを使用する必要があります  \(キーに文字列を使用する場合、大文字と小文字が区別されることに注意してください\)。2 つ目は、ディクショナリの値はオブジェクトであるため、プロパティ値を取得するときにその値を目的の型に変換する必要があります。  
  
## 参照  
 <xref:System.Windows.ResourceDictionary>   
 <xref:System.Windows.Application.Resources%2A>   
 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [マージされたリソース ディクショナリ](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)