Design Diagram using Visitor Pattern:

![image](https://user-images.githubusercontent.com/109504231/181691304-19311e08-a39d-4ffd-b5dc-52e1a4fc8b37.png)


Code to implement the problem:

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace DesignPatternPractice
{
	//Object Structure
	public class Image
	{

		List<Shape> _structure = new List<Shape>();
		public void Plot(List<ShapePlotter> plotters)
		{
			foreach (ShapePlotter p in plotters)
			{
				foreach (Shape s in _structure)
				{
					s.Plot(p);
				}
			}

			//M*N cartesian product
			
		}


	}
	public abstract class Shape
	{
		public abstract void Plot(ShapePlotter shapePlotter);
	}

	public abstract class Rectangle : Shape
	{
		public string GeHeightAndWidth() { return "R.H.W"; }
        public override void Plot(ShapePlotter shapePlotter)
        {
			shapePlotter.Plot(this);
		}
    }
	public abstract class Circle : Shape
	{
		public string GetRadius() { return "C.R"; }
		public override void Plot(ShapePlotter shapePlotter)
		{
			shapePlotter.Plot(this);
		}
	}
	public abstract class Polygon : Shape
	{
		public string GetSides() { return "P.S"; }
		public override void Plot(ShapePlotter shapePlotter)
		{
			shapePlotter.Plot(this);
		}
	}

	public abstract class ShapePlotter
	{
		public abstract void Plot(Rectangle rectangle);
		public abstract void Plot(Circle circle);
		public abstract void Plot(Polygon polygon);
	}

    public class LaserPrinter : ShapePlotter
    {
        public override void Plot(Rectangle rectangle)
        {
            throw new NotImplementedException();
        }

        public override void Plot(Circle circle)
        {
            throw new NotImplementedException();
        }

        public override void Plot(Polygon polygon)
        {
            throw new NotImplementedException();
        }
    }
    public class InkJetrinter : ShapePlotter
    {
		public override void Plot(Rectangle rectangle)
        {
            throw new NotImplementedException();
        }

		public override void Plot(Circle circle)
        {
            throw new NotImplementedException();
        }

		public override void Plot(Polygon polygon)
        {
            throw new NotImplementedException();
        }
    }
}
