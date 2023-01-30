# Lecture5Answers


2.

        // Inserts the given date into the list in chronological order.
        // Precondition: list is already sorted in chronological order.   
        public static void insert(ArrayList<CalendarDate> list, CalendarDate date)
        {
		// Find the first date in the list that is later than the 
		// date given in the parameter
                int index = 0;
                while (index < list.size() 
                                && list.get(index).compareTo(date) < 0)
                        index++;

		// Insert the date into the list at this position
		// (the add method will shift over the dates to make room)
                list.add(index, date);
        }  


3.

       public boolean add(T newEntry) {
           
                // Search for index for insert point in array
                int index = 0;
                while (index < numData &&
                                dataArray[index].compareTo(newEntry) <= 0) {
                        if (dataArray[index].compareTo(newEntry) == 0)
                                return false;   // duplicate entry - do not insert
                        index++;
                }
         
                // Check for full array: Why isn't this done before the while loop?
                if (numData == dataArray.length)
                        reallocate();

                // Shift data over one position to make room for new data 
                // data value at position index.                
                for (int position = numData-1; position >= index; position--) 
                       dataArray[position+1] = dataArray[position];
                dataArray[index] = newEntry;
                numData++;
                return true;
        }                
