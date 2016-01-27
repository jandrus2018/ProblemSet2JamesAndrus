# ProblemSet2JamesAndrus

// 1.3.19
	public void removeLast() {
		if (isEmpty()) {
		} else if (N == 1) {
			first = null;
			N = 0;
		} else {
			Node temp = first;
			while (temp.next.next != null) {
				temp = temp.next;
			}
			N--;
			temp.next = null;
		}
	}
	
	
	// 1.3.20
	public void delete(int k) {
		if (k > N || k == 0) {
			System.out.println("Element at " + k + " does not exist.");
		} else if (N == k) {
			removeLast();
		} else if (k == 1) {
			first = first.next;
			N--;
		} else {
			Node temp = first;
			int count = 2;
			while (count < k) {
				temp = temp.next;
				count++;
			}
			N--;
			temp.next = temp.next.next;
		}

	}
	
	
	// 1.3.21
	public boolean find(String key /* , LinkedList list */) {
		if (isEmpty()) {
			return false;
		}
		Node temp = first; // Node temp = list.first;
		while (temp.next != null) {
			if (temp.item.equals(key)) {
				return true;
			}
			temp = temp.next;
		}
		if (temp.item.equals(key)) {
			return true;
		}
		return false;

	}
	
	
	//1.3.24
	public static void removeAfter(LinkedList list, Node node) {
		Node first = list.getFirst();
		if (node == first) {
			first.next = first.next.next;
			N--;
		} else if (node.next == null || node == null) {
			//do nothing
		} else if (node.next.next == null) {
			removeLast();
		}
		else {
			Node temp = first;
			while (temp != node) {
				temp = temp.next;
			}
			temp.next = temp.next.next;
			N--;
		}
	}
	
	
	// 1.3.25
	public void insertAfter(Node targetNode, Node insertNode) {
		if (targetNode == null || insertNode == null) {
			// do nothing
		} else {
			Node temp = first;
			while (temp != targetNode) {
				temp = temp.next;
			}
			if (temp == targetNode) {
				insertNode.next = temp.next;
				temp.next = insertNode;
				N++;
			}
		}
	}
	
	
	//The fun one
	// 1.3.26
		public void remove(/* LinkedList<String> list, */ String key) {
			while (first != null && first.item.equals(key)) {
				first = first.next; // Changed to list.first
				N--;
			}
			Node current = first;
			Node trail = null;

			while (current != null) {
				if (current.item.equals(key)) {
					trail.next = current.next;
					current = current.next;
					N--;
				} else {
					trail = current;
					current = current.next;
				}
			}
		}
