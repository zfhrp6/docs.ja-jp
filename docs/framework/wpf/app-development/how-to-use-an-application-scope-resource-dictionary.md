---
title: '方法 : アプリケーション スコープのリソース ディクショナリを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: a42fee8ad31dcc02459711fc51e8611e0e8cd012
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547051"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>方法 : アプリケーション スコープのリソース ディクショナリを使用する
この例では、アプリケーション スコープのカスタム リソース ディクショナリを定義して、使用する方法を示します。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Application> 共有リソースのアプリケーション スコープのストアを公開:<xref:System.Windows.Application.Resources%2A>です。 既定では、<xref:System.Windows.Application.Resources%2A>プロパティは、のインスタンスを初期化、<xref:System.Windows.ResourceDictionary>型です。 Get を使用してアプリケーション スコープのプロパティを設定すると、このインスタンスを使用する<xref:System.Windows.Application.Resources%2A>です。 詳細については、次を参照してください。[する方法: を取得し、アプリケーション スコープ リソース設定](http://msdn.microsoft.com/library/39e0420c-c9fc-47dc-8956-fdd95b214095)です。
  
 複数のリソースを使用して設定する必要がある場合<xref:System.Windows.Application.Resources%2A>、それらのリソースを格納および設定する代わりに、カスタム リソース ディクショナリを使用できます<xref:System.Windows.Application.Resources%2A>して代わりにします。 XAML を使用して、カスタム リソース ディクショナリを宣言する方法を次に示します。
  
 [!code-xaml[HOWTOResourceDictionaries#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 使用して全体のリソース ディクショナリのスワップ<xref:System.Windows.Application.Resources%2A>各テーマが 1 つのリソース ディクショナリでカプセル化された場所を使用すると、アプリケーション スコープのテーマをサポートします。 <xref:System.Windows.ResourceDictionary> を設定する方法を次の例に示します。  
  
 [!code-xaml[HOWTOResourceDictionaries#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 によって公開されるリソース ディクショナリからアプリケーション スコープのリソースを取得する方法を次に示します<xref:System.Windows.Application.Resources%2A>XAML でします。  
  
 [!code-xaml[HOWTOResourceDictionaries#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 コードでリソースも取得する方法を次に示します。  
  
 [!code-csharp[HOWTOResourceDictionaries#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 2 つの考慮事項を使用する場合がある<xref:System.Windows.Application.Resources%2A>です。 まず、ディクショナリ*キー*オブジェクトは両方の設定とプロパティ値を取得するときに正確に同じオブジェクト インスタンスを使用する必要があります。 (キーに文字列を使用する場合、大文字と小文字が区別されることに注意してください)。2 番目、ディクショナリ*値*がオブジェクト、プロパティ値を取得するときに、値を目的の型に変換しなければならないためです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.ResourceDictionary>  
 <xref:System.Windows.Application.Resources%2A>  
 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [マージされたリソース ディクショナリ](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)
