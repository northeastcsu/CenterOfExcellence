---
title: "Test Snippet"
author: "Microsoft"
categories: code
tags: ['code', 'c#']
description: "Test snippet of code"
image: 
solution_url:
---
```CSharp
public static async void GetProjects()
{
 try
 {
  var personalaccesstoken = "PAT_FROM_WEBSITE";

  using (HttpClient client = new HttpClient())
  {
   client.DefaultRequestHeaders.Accept.Add(
    new System.Net.Http.Headers.MediaTypeWithQualityHeaderValue("application/json"));

   client.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Basic",
    Convert.ToBase64String(
     System.Text.ASCIIEncoding.ASCII.GetBytes(
      string.Format("{0}:{1}", "", personalaccesstoken))));

   using (HttpResponseMessage response = await client.GetAsync(
      "https://dev.azure.com/{organization}/_apis/projects"))
   {
    response.EnsureSuccessStatusCode();
    string responseBody = await response.Content.ReadAsStringAsync();
    Console.WriteLine(responseBody);
   }
  }
 }
 catch (Exception ex)
 {
  Console.WriteLine(ex.ToString());
 }
}
```
