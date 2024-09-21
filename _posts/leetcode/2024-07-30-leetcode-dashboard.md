---
title: LeetCode Summary by Topics
description: Collection of summarized notes and key problem-solving techniques for various LeetCode topics. 
pin: true
author: yoyo
date: 2024-07-30 02:30:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Leetcode Summary]
tags: []
---

> <details>
>  <summary><strong>Navigation Tips</strong></summary>
>  <ul>
>    <li>Use the <strong>search feature</strong> in your browser (Ctrl + F or Command + F) to quickly find specific days or topics.> > </li>
>    <li>Bookmark this page for easy access in the future.</li>
>  </ul>
> </details>
{: .prompt-info }

<details>
  <summary><strong>Full list of Leetcode questions</strong></summary>

<table>
  <thead>
    <tr>
      <th>Topic</th>
      <th>Link to the problem sets</th>
    </tr>
  </thead>
  <tbody>
    {% assign topics = "Array,Linked List,Hash Table,String,Stack and Queue,Binary Tree,Backtracking,Greedy,Dynamic Programming,Monotone stack,Graph Theory" | split: ',' %}
    
    {% for topic in topics %}
    <tr>
      <td><strong><a href="#{{ topic | downcase | replace: ' ', '-' }}">{{ topic }}</a></strong></td>
      <td>
        {% for post in site.posts %}
          {% if topic == post.categories[-1] %}
            <a href="{{ post.url }}">{{ post.title }}</a> <br>
          {% endif %}
        {% endfor %}
      </td>
    </tr>
    {% endfor %}
  </tbody>
</table>  
</details>



## Array

<details>
  <summary><strong>Array questions</strong></summary>
{% include category-post-scroll.html category="Array" scroll=true %}
</details>

## Linked List

<details>
  <summary><strong>Linked List questions</strong></summary>
{% include category-post-scroll.html category="Linked List" scroll=true %}
</details>

## Hash Table

<details>
  <summary><strong>Hash Table questions</strong></summary>
{% include category-post-scroll.html category="Hash Table" scroll=true %}
</details>

## String

<details>
  <summary><strong>String questions</strong></summary>
{% include category-post-scroll.html category="String" scroll=true %}
</details>

## Stack and Queue

<details>
  <summary><strong>Stack and Queue questions</strong></summary>
{% include category-post-scroll.html category="Stack and Queue" scroll=true %}
</details>

## Binary Tree

<details>
  <summary><strong>Binary Tree questions</strong></summary>
{% include category-post-scroll.html category="Binary Tree" scroll=true %}
</details>

## Backtracking

<details>
  <summary><strong>Backtracking questions</strong></summary>
{% include category-post-scroll.html category="Backtracking" scroll=true %}
</details>

## Greedy

<details>
  <summary><strong>Greedy questions</strong></summary>
{% include category-post-scroll.html category="Greedy" scroll=true %}
</details>

## Dynamic Programming

<details>
  <summary><strong>Dynamic Programming questions</strong></summary>
{% include category-post-scroll.html category="Dynamic Programming" scroll=true %}
</details>

## Monotone stack

<details>
  <summary><strong>Monotone stack questions</strong></summary>
{% include category-post-scroll.html category="Monotone stack" scroll=true %}
</details>

## Graph Theory

<details>
  <summary><strong>Graph theory questions</strong></summary>
{% include category-post-scroll.html category="Graph Theory" scroll=true %}
</details>

