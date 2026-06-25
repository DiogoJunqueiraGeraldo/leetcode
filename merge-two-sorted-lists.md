Link: https://leetcode.com/problems/merge-two-sorted-lists/submissions/2045174994/


```go
import "cmp"
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func mergeTwoLists(l1 *ListNode, l2 *ListNode) *ListNode {
    if l1 == nil || l2 == nil { return cmp.Or(l1, l2) }

    if l1.Val <= l2.Val {
        l1.Next = mergeTwoLists(l1.Next, l2)
        return l1
    } else {
        l2.Next = mergeTwoLists(l1, l2.Next)
        return l2
    }
}
```

Submission: https://leetcode.com/problems/merge-two-sorted-lists/submissions/2045178037/
```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* mergeTwoLists(struct ListNode* list1, struct ListNode* list2) {
    if (list1 == NULL) { return list2; }

    if (list2 == NULL) { return list1; }

    if (list1->val <= list2->val) {
        list1->next = mergeTwoLists(list1->next, list2);
        return list1;
    } else {
        list2->next = mergeTwoLists(list1, list2->next);
        return list2;
    }
}
```

Submission: https://leetcode.com/problems/merge-two-sorted-lists/submissions/2045185471/
```c
#define ever ;;

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* mergeTwoLists(struct ListNode* list1, struct ListNode* list2) {
    if (list1 == NULL) { return list2; }

    if (list2 == NULL) { return list1; }

    struct ListNode *head, *curr, *other;
    if (list1 -> val <= list2 -> val) {
        head = curr = list1;
        other = list2;
    }  else {
        head = curr = list2;
        other = list1;
    }

    for(ever) {
        if (curr == NULL || other == NULL) {
            break;
        }

        if (curr -> next != NULL && curr -> next -> val <= other -> val) {
            curr = curr->next;
        } else {
            struct ListNode *aux = curr -> next;
            curr -> next = other;
            other = aux;
        }
    }

    return head;
}
```