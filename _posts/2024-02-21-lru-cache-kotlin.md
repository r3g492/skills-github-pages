---
title: "lru-cache"
date: 2024-02-21
layout: post
---

```kotlin
class LRUCache(capacity: Int) {
    val cap = capacity
    private val map: MutableMap<Int, Node> = mutableMapOf()

    private var head: Node? = null
    private var tail: Node? = null

    class Node(
        val key: Int,
        val value: Int,
        var prev: Node? = null,
        var next: Node? = null,
    ) {
        override fun toString(): String {
            return "Node(key=$key, value=$value, prev=${prev?.key}, next=${next?.key})"
        }
    }

    fun get(key: Int): Int {
        val foundNode = map[key]
        val answer = if (foundNode == null) {
            -1
        } else {
            deleteFromList(foundNode)
            val newNode = Node(
                key = key,
                value = foundNode.value
            )
            appendToList(newNode)
            foundNode.value
        }

        // printFromHead()
        // println(answer)
        return answer
    }

    fun put(key: Int, value: Int) {
        val newNode = Node(
            key = key,
            value = value
        )
        val duplication = map[key]
        if (duplication != null) {
            deleteFromList(duplication)
        }
        appendToList(newNode)

        if (map.size > cap) {
            deleteFromList(head!!)
        }
    }

    private fun appendToList(node: Node) {
        if (head == null || tail == null) {
            head = node
            tail = node
            map[node.key] = node
            return
        }

        tail!!.next = node
        node.prev = tail
        tail = node

        map[node.key] = node
    }

    private fun deleteFromList(node: Node) {
        val prevNode = node.prev
        val nextNode = node.next
        prevNode?.next = nextNode
        nextNode?.prev = prevNode

        if (node == head) {
            head = nextNode
        }
        if (node == tail) {
            tail = prevNode
        }

        map.remove(node.key)
    }

    private fun printFromHead() {
        var cur = head
        println("map : $map")
        while (cur != null) {
            println("cur = ${cur.key}, ${cur.value}")
            cur = cur.next
        }
    }
}
```
