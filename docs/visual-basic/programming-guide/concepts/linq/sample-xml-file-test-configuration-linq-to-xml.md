---
title: 'サンプル XML ファイル : テスト構成 (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2e0e19f2-83e4-42ad-958a-6b3e34c9bf17
ms.openlocfilehash: 938916d568558738a703206d98fe42faca072f02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sample-xml-file-test-configuration-linq-to-xml"></a><span data-ttu-id="84b31-102">サンプル XML ファイル : テスト構成 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="84b31-102">Sample XML File: Test Configuration (LINQ to XML)</span></span>
<span data-ttu-id="84b31-103">次の XML ファイルは、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ドキュメントのさまざまな例で使用されます。</span><span class="sxs-lookup"><span data-stu-id="84b31-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="84b31-104">これはテスト構成ファイルです。</span><span class="sxs-lookup"><span data-stu-id="84b31-104">This is a test configuration file.</span></span>  
  
## <a name="testconfigxml"></a><span data-ttu-id="84b31-105">TestConfig.xml</span><span class="sxs-lookup"><span data-stu-id="84b31-105">TestConfig.xml</span></span>  
  
```xml  
<?xml version="1.0"?>  
<Tests>  
  <Test TestId="0001" TestType="CMD">  
    <Name>Convert number to string</Name>  
    <CommandLine>Examp1.EXE</CommandLine>  
    <Input>1</Input>  
    <Output>One</Output>  
  </Test>  
  <Test TestId="0002" TestType="CMD">  
    <Name>Find succeeding characters</Name>  
    <CommandLine>Examp2.EXE</CommandLine>  
    <Input>abc</Input>  
    <Output>def</Output>  
  </Test>  
  <Test TestId="0003" TestType="GUI">  
    <Name>Convert multiple numbers to strings</Name>  
    <CommandLine>Examp2.EXE /Verbose</CommandLine>  
    <Input>123</Input>  
    <Output>One Two Three</Output>  
  </Test>  
  <Test TestId="0004" TestType="GUI">  
    <Name>Find correlated key</Name>  
    <CommandLine>Examp3.EXE</CommandLine>  
    <Input>a1</Input>  
    <Output>b1</Output>  
  </Test>  
  <Test TestId="0005" TestType="GUI">  
    <Name>Count characters</Name>  
    <CommandLine>FinalExamp.EXE</CommandLine>  
    <Input>This is a test</Input>  
    <Output>14</Output>  
  </Test>  
  <Test TestId="0006" TestType="GUI">  
    <Name>Another Test</Name>  
    <CommandLine>Examp2.EXE</CommandLine>  
    <Input>Test Input</Input>  
    <Output>10</Output>  
  </Test>  
</Tests>  
```  
  
## <a name="see-also"></a><span data-ttu-id="84b31-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="84b31-106">See Also</span></span>  
 [<span data-ttu-id="84b31-107">サンプル XML ドキュメント (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="84b31-107">Sample XML Documents (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
